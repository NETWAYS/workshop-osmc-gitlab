!SLIDE smbullets
# GitLab CI

* Build Pipelines
* Natively integrated into GitLab
* Invokes GitLab Runners
* Local container registry for runners


~~~SECTION:handouts~~~

****

Documentation: https://docs.gitlab.com/ce/ci/README.html

Reference example (German): https://blog.netways.de/2017/05/03/gitlab-ce-continuous-integration-jobs-and-runners/

~~~ENDSECTION~~~

!SLIDE smbullets
# GitLab CI: Introduction

* `.gitlab-ci.yml` configuration file in Git repository
* Runner is triggered on specific events, e.g. `git push`
* Jobs can be run on-demand
* Built-in and external runners
* Container registry enabled for the project (optional)


~~~SECTION:handouts~~~

****

Documentation references:

https://docs.gitlab.com/ce/user/project/container_registry.html

~~~ENDSECTION~~~


!SLIDE smbullets
# GitLab Runners

* Written in Go
* Linux/Unix, macOS, Windows, Docker support
* Run multiple jobs in parallel
* Run jobs locally, in Docker containers, remote via SSH
* Can run Bash, Windows Batch/Powershell


~~~SECTION:handouts~~~

****

Documentation reference: https://docs.gitlab.com/runner/

~~~ENDSECTION~~~


!SLIDE smbullets
# GitLab Runners: Installation and Configuration

* Separate server
* Installation via package repository
* `gitlab-runner register`

This comes pre-installed in the NWS apps.

~~~SECTION:handouts~~~

****

Documentation References:

https://docs.gitlab.com/runner/install/linux-repository.html
https://docs.gitlab.com/runner/register/index.html

~~~ENDSECTION~~~


!SLIDE smbullets
# GitLab CI: Docker, Containers - how to use it

* Run an application in an isolated environment
* Layered images providing additional libraries and tools, e.g. base linux, mysql, apache, ruby
* Start container, run tests, return results
* Light-weight and fast, can run on each Git push
* Reliable same run each time, container is destroyed on stop


~~~SECTION:handouts~~~

****

Documentation References:

https://docs.docker.com


~~~ENDSECTION~~~

!SLIDE smbullets noprint
# GitLab CI: Docker and CI Runners

<center><img src="../../_images/ci/git_gitlab_ci_runners_docker.png" alt="GitLab CI Runners Docker"/></center>

!SLIDE smbullets printonly
# GitLab CI: Docker and CI Runners

<center><img src="../../_images/ci/git_gitlab_ci_runners_docker.png" style="width:450px" alt="GitLab CI Runners Docker"/></center>

~~~SECTION:handouts~~~

****

Documentation References:

https://docs.docker.com
https://docs.gitlab.com/runner/install/docker.html

~~~ENDSECTION~~~



!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Inspect CI Runner settings

* Objective:
 * Inspect CI Runner Settings
* Steps:
 * Navigate to Admin > Overview > Runners
 * Inspect the token
 * Check existing runners


~~~SECTION:handouts~~~

****

Reference: https://gitlab.com/gitlab-org/gitlab-runner/blob/master/docs/install/linux-repository.md



~~~ENDSECTION~~~


!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Open Runner Administration View

****

Navigate to `/admin/runners`.

```
How to setup a shared Runner for a new project
Install a Runner compatible with GitLab CI (checkout the GitLab Runner section for information on how to install it).
Specify the following URL during the Runner setup: ...
Use the following registration token during setup: ...
Start the Runner!
```

### Runners

Registered runners are listed at the bottom.

#### Register Runner

* Steps:
 * Run `gitlab-runner register` as root
 * Use the HTTP Url as host
 * Paste the token
 * Add description `training01` and tag `training`
 * Untagged builds: `true`, Lock to current project: `false`
 * Executor: `docker`, Default: `alpine:latest`


Reference: https://gitlab.com/gitlab-org/gitlab-runner/blob/master/docs/install/linux-repository.md
Reference: https://docs.gitlab.com/runner/install/linux-repository.html

Reference for Docker: https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/

Example on Ubuntu:

```
apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

apt-get update
apt-get install docker-ce
```

```
curl -L https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh | sudo bash
apt-get install gitlab-runner
```


Start CLI

    @@@ Sh
    # gitlab-runner register
    Running in system-mode.

    Please enter the gitlab-ci coordinator URL (e.g. https://gitlab.com/):
    http://192.168.56.101

    Please enter the gitlab-ci token for this runner:
    Do1aqTvPiiBj6_u_u5Ye

    Please enter the gitlab-ci description for this runner:
    [ubuntu-16]: training01

    Please enter the gitlab-ci tags for this runner (comma separated):
    training

    Whether to run untagged builds [true/false]:
    [false]: true

    Whether to lock the Runner to current project [true/false]:
    [true]: false
    Registering runner... succeeded                     runner=Do1aqTvP

    Please enter the executor: docker+machine, docker-ssh, parallels, ssh, virtualbox, docker, shell, docker-ssh+machine, kubernetes:
    docker

    Please enter the default Docker image (e.g. ruby:2.1):
    alpine:latest

    Runner registered successfully. Feel free to start it, but if it's running already the config should be automatically reloaded!


!SLIDE smbullets
# GitLab CI: Configuration in .gitlab-ci.yml

* `image` as container base image
* `services` which should be running
* `all_tests` as job name

Example:

    image: centos:7

    all_tests:
      script:
        - exit 1

~~~SECTION:handouts~~~

****

Documentation References:

https://about.gitlab.com/2016/03/01/gitlab-runner-with-docker/


~~~ENDSECTION~~~

!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Issue: Add CI

* Objective:
 * Create a new issue for adding CI before 1.0.0 release
* Steps:
 * Create a new issue "Add CI"
 * Description contains a bullet list with `- [ ] GitLab CI configuration`.
 * Add to milestone `1.0.0`

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Issue: Add CI

****

Follow the instructions and ask the trainer for help in case.

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~


!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Create .gitlab-ci.yml

* Objective:
 * Create CI configuration for the training project
* Steps:
 * Navigate to `Project > Details`
 * Click on `Set up CI/CD`
 * Edit the `.gitlab-ci.yml` file using the Web IDE
 * Add `image: centos:7` to specify base image
 * Add job `all_tests` with `script` as array element, which itself runs `exit 1`
* Merge Request:
 * Target branch: `feature/ci` - new merge request
 * Create the merge request
 * Description: `fixes #1` to auto-close the issue on merge


~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Create .gitlab-ci.yml file

****

### Create CI configuration file

    @@@ Sh
    image: centos:7

    all_tests:
      script:
        - exit 1

The script will always fail. We will use different exit states to fix it.
Future examples and tests work the same way.

!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Fix failed Merge Request

* Objective:
 * Create Merge Request from .gitlab-ci.yml file
* Steps:
* Next steps:
 * Open the Merge Request where CI failed
 * Click on `Open in Web IDE` to modify the changes again
 * Fix the exit code to `0`, commit the change
 * Inspect the CI status with the rocket icon on the right
 * Once tests are green, merge to master
 * Open the `Add CI` issue

**Tip**: You can test and fix the CI config in branches
triggering CI again. CI Inception ;-)

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~


!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Fix failed Merge Request

Follow the trainer instructions.

    @@@ Sh
    image: centos:7

    all_tests:
      script:
    -    - exit 1
    +    - exit 0


