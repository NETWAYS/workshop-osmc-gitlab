!SLIDE smbullets
# Jobs, Stages, Pipelines

* Compile
* Test
* Package
* Test package
* Upload/Deploy

!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Our Go App

* Objective:
 * Create an app in Go
* Steps:
 * Navigate into `Project > Details` and open the Web IDE
 * Create a new file called `main.go`
 * Commit the change to `feature/go-app` and create a MR with milestone `1.0.0`

main.go:

    package main

    func main() {
        fmt.Println("Hello from OSMC")
    }

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Our Go App

****

Follow the instructions and ask the trainer for help in case.

main.go

    package main

    func main() {
        fmt.Println("Hello from OSMC")
    }


~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~


!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Build the Go App with CI

* Objective:
 * Our Go code may or may not work - test it
* Steps:
 * Navigate to `Repository > Branches`
 * Select `feature/go-app`, open `.gitlab-ci.yml` and edit with the Web IDE
 * Select `Go` from the `Choose a template` dropdown (fallback: https://docs.gitlab.com/ee/ci/examples/README.html)
 * Edit `REPO_NAME` with the URL to your project (without `https://`)
 * **Replace `mybinary` with `go-app`**
 * Commit the changes and inspect CI on the right

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Build the Go App with CI

****

Follow the instructions and ask the trainer for help in case.

The resulting .gitlab-ci.yml looks like this:

    # This file is a template, and might need editing before it works on your project.
    image: golang:latest
    
    variables:
      # Please edit to your GitLab project
      REPO_NAME: 4014-gitlab-b1d71-web.nws.netways.de/osmc/workshop
    
    # The problem is that to be able to use go get, one needs to put
    # the repository in the $GOPATH. So for example if your gitlab domain
    # is gitlab.com, and that your repository is namespace/project, and
    # the default GOPATH being /go, then you'd need to have your
    # repository in /go/src/gitlab.com/namespace/project
    # Thus, making a symbolic link corrects this.
    before_script:
      - mkdir -p $GOPATH/src/$(dirname $REPO_NAME)
      - ln -svf $CI_PROJECT_DIR $GOPATH/src/$REPO_NAME
      - cd $GOPATH/src/$REPO_NAME
    
    stages:
      - test
      - build
      - deploy
    
    format:
      stage: test
      script:
        - go fmt $(go list ./... | grep -v /vendor/)
        - go vet $(go list ./... | grep -v /vendor/)
        - go test -race $(go list ./... | grep -v /vendor/)
    
    compile:
      stage: build
      script:
        - go build -race -ldflags "-extldflags '-static'" -o $CI_PROJECT_DIR/go-app
      artifacts:
        paths:
          - go-app


Build fails since we miss an import from `fmt`.

    $ mkdir -p $GOPATH/src/$(dirname $REPO_NAME)
    $ ln -svf $CI_PROJECT_DIR $GOPATH/src/$REPO_NAME
    
    '/go/src/4014-gitlab-b1d71-web.nws.netways.de/osmc/workshop' -> '/builds/osmc/workshop'
    $ cd $GOPATH/src/$REPO_NAME
    
    $ go fmt $(go list ./... | grep -v /vendor/)
    
    main.go
    $ go vet $(go list ./... | grep -v /vendor/)
    
    # 4014-gitlab-b1d71-web.nws.netways.de/osmc/workshop
    vet: ./main.go:4:2: undeclared name: fmt
    ERROR: Job failed: exit code 1


~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~


!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Fix the error and inspect the Pipeline

* Objective:
 *  Add missing import, inspect CI pipeline
* Steps:
 * Navigate to `Repository > Branches`
 * Open the `main.go` file with the Web IDE and add the import after the package declaration
 * Commit the change and inspect CI on the right again

main.go:

    package main

    import (
        "fmt"
    )


~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Fix the error and inspect the Pipeline

****

Follow the instructions and ask the trainer for help in case.

    package main
    
    import (
        "fmt"
    )
    
    func main() {
        fmt.Println("Hello from OSMC")
    }


~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~


!SLIDE smbullets

# Summary

* Configuration in .gitlab-ci.yml
* Execute scripts in defined jobs
* Pass variables to job runs
* A complete development build pipeline with a Go app

We did not merge the MR to master yet. Everything is developed
in our `feature/go-app` branch and does not influence other collaborators.



~~~SECTION:handouts~~~

****



~~~ENDSECTION~~~
