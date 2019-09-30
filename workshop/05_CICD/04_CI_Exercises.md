!SLIDE smbullets
# Jobs, Stages, Pipelines

* Compile
* Test
* Package
* Test package
* Upload/Deploy


!SLIDE smbullets small
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Practical Example for CI Runners: Preparations

* Objectives:
 * Prepare container to convert Markdown to HTML
* Steps:
 * Modify `.gitlab-ci.yml` and add a `before_script` section after the `image` section
 * Update `apk` package manager and install `python` and `py-pip` packages
 * Use `pip` to install the `markdown` and `Pygments` libraries
 * Commit and push the changes

Example:

    before_script:
      - apk update && apk add python py-pip
      - pip install markdown Pygments

~~~SECTION:handouts~~~

****

The base image uses Alpine Linux which has a very small installation size
and footprint.

In contrast to the "typical" Linux distribution containers, this allows for
faster tests and deployment scripts.

If your build pipeline involves specific distributions, choose the best and
reliable container distribution you prefer.

Alpine uses its own package manager. This exercise installs

* Python and its package manager `pip`
* Markdown conversion packages for Python

Reference: https://wiki.alpinelinux.org/wiki/Alpine_Linux_package_management

~~~ENDSECTION~~~


!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Prepare container to convert Markdown to HTML

****

### Edit .gitlab-ci.yml and add before_script

    @@@ Sh
    $ vim .gitlab-ci.yml

    image: alpine:latest

    before_script:

### Update apk and install Python/pip

    @@@ Sh
    $ vim .gitlab-ci.yml

    image: alpine:latest

    before_script:
      - apk update && apk add python py-pip

### Install Markdown Python libraries

    @@@ Sh
    $ vim .gitlab-ci.yml

    image: alpine:latest

    before_script:
      - apk update && apk add python py-pip
      - pip install markdown Pygments

### Verify the content

    @@@ Sh
    $ vim .gitlab-ci.yml

    image: alpine:latest

    before_script:
      - apk update && apk add python py-pip
      - pip install markdown Pygments

    all_tests:
      script:
        - exit 0

### Commit and push the changes

    @@@ Sh
    $ git commit -av -m "CI: Prepare markdown conversion"
    $ git push


!SLIDE smbullets small
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Practical Example for CI Runners: Create Docs

* Objective:
 * Create HTML docs from Markdown
* Steps:
 * Add a new `markdown` and use `script` to generate `README.html`
 * Add `artifacts` with `paths` pointing to `README.html`. Expires in `1 week`
 * Commit and push the changes, then download and view the `README.html` file in your browser

Example:

    markdown:
      script:
        - python -m markdown README.md > README.html
      artifacts:
        paths:
        - README.html
        expire_in: 1 week

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~


!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Create HTML docs from Markdown

****

### Edit .gitlab-ci.yml and add markdown section

    @@@ Sh
    $ vim .gitlab-ci.yml

    ...

    all_tests:
      script:
        - exit 0

    markdown:

### Add script to convert Markdown into HTML

    @@@ Sh
    $ vim .gitlab-ci.yml

    ...

    markdown:
      script:
        - python -m markdown README.md > README.html

### Store artifacts

Add `paths` section which includes `README.html` as entry.
Tell GitLab to expire this artifact in `1 week`.

    @@@ Sh
    $ vim .gitlab-ci.yml

    ...

    markdown:
      script:
        - python -m markdown README.md > README.html
      artifacts:
        paths:
        - README.html
        expire_in: 1 week

### Verify the content

    @@@ Sh
    $ vim .gitlab-ci.yml

    image: alpine:latest

    before_script:
      - apk update && apk add python py-pip
      - pip install markdown Pygments

    all_tests:
      script:
        - exit 0

    markdown:
      - python -m markdown README.md > README.html
      artifacts:
        paths:
        - README.html
        expire_in: 1 week

### Commit and push the changes

    @@@ Sh
    $ git commit -av -m "CI: Generate HTML docs from Markdown"
    $ git push

### Download HTML artifacts

Navigate into the repository > `CI / CD` > Jobs > `#...`  and choose `Job Artifacts`.
Download them, extract them and open the HTML file with your browser.

!SLIDE smbullets small
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Practical Example for CI Runners: Update Docs

* Objective:
 * Add what you have learned so far into README.md and generate docs
* Steps:
 * Edit `README.md`
 * Commit and push changes
 * Download and view the `README.html` file in your browser


~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~


!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Update docs

****

### Edit README.md and add learned details

    @@@ Sh
    vim README.md

    # CI Runners

    ....

### Commit and push changes

    @@@ Sh
    git commit -av -m "Add notes on CI runners"
    git push

### Download HTML artifacts

Navigate into the repository > `CI / CD` > Jobs > `#...`  and choose `Job Artifacts`.
Download them, extract them and open the HTML file with your browser.




!SLIDE smbullets
# GitLab CI: .gitlab-ci.yml Templates

* Repository: https://gitlab.com/gitlab-org/gitlab-ce/tree/master/lib/gitlab/ci/templates
 * PHP
 * C++
 * Go
 * Python

~~~SECTION:handouts~~~

****

Documentation References:

https://docs.gitlab.com/ce/ci/README.html#examples

https://gitlab.com/gitlab-org/gitlab-ci-yml


~~~ENDSECTION~~~


!SLIDE smbullets
# GitLab CI: Variables

* Variables accessible in the Job container
 * Pre-defined environment variables
 * User-defined project variables
 * .gitlab-ci.yml defined variables

https://docs.gitlab.com/ce/ci/variables/

~~~SECTION:handouts~~~

****



~~~ENDSECTION~~~

