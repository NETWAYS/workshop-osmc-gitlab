!SLIDE smbullets
# Artifacts and Caches

* Artifacts
  * Files generated from jobs in containers
  * Passed between stages
  * Made available via `artifacts` stored in GitLab's database
* Caches
  * Share cached directories between jobs
  * Build job generates tarball, Package job creates RPM from tarball
  * Cache Git tree with artificats e.g. for C++ & ccache to reduce build times

https://docs.gitlab.com/ce/ci/caching/

~~~SECTION:handouts~~~

****



~~~ENDSECTION~~~


!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Inspect Artifacts

* Objective:
 * Learn more about `artifacts` configuration and location
* Steps:
 * Open `.gitlab-ci.yml` and search for `artifacts`
 * `script` generates a binary inside the container
 * `artifact` exports this to GitLab
 * Open `CI / CD > Pipelines` with the last run, select `compile` job
 * Browse the `Job artifacts` on the right
 * Download the binary and run it

Hint for trainer with macOS

    chmod +x ~/Downloads/go-app
    docker run -ti -v ~/Downloads:/mnt ubuntu:bionic bash
    ./mnt/go-app

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Inspect Artifacts

****

Follow the instructions and ask the trainer for help in case.

.gitlab-ci.yml

    compile:
      stage: build
      script:
        - go build -race -ldflags "-extldflags '-static'" -o $CI_PROJECT_DIR/go-app
      artifacts:
        paths:
          - go-app



~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~
