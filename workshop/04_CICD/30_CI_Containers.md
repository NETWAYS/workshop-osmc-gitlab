!SLIDE smbullets
# GitLab CI: Container Registry

* Enable the Container Registry (administration server setting)
* Enable the Container Registry for the project
* Advanced usage only

https://docs.gitlab.com/ce/ci/docker/using_docker_build.html

~~~SECTION:handouts~~~

****

   @@@ Sh
   $ vim /etc/gitlab/gitlab.rb

   registry_external_url 'https://gitlab.example.com:5000'

   $ gitlab-ctl reconfigure

Documentation References:

https://docs.gitlab.com/ce/user/project/container_registry.html
https://docs.gitlab.com/ce/administration/container_registry.html
~~~ENDSECTION~~~


!SLIDE smbullets
# Create Docker Image and Push to Container Registry

* Use the "Docker in Docker Workflow"
  * Starts a virtual Docker service which maps the outside Docker daemon
  * Run privileged job scripts to create a Docker image
  * Push the image to the CI registry
* New repository contains
  * Dockerfile and tools for building the image
  * .gitlab-ci.yml starting `dind` service, build and push actions

The Docker registry in the NWS GitLab app is already enabled.

    docker login -u root 4014-gitlab-b1d71-registry.nws.netways.de

https://docs.gitlab.com/ee/ci/docker/using_docker_build.html

~~~SECTION:handouts~~~

****


~~~ENDSECTION~~~


!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Create a new project for Container Builds

* Objective:
 * Create a new project `docker-fpm` in the `osmc` group
* Steps:
 * Click the `+` icon from the header menu, select `new project`
 * Project name `docker-fpm`
 * Description: `Create a Docker image and push to our registry`

The Docker image should run the `fpm` binary which can be used to build
packages. Note: Advanced packaging for RPM/DEB should be done with
distribution specific package tools.

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Create a new project for Container Builds

****

Follow the instructions and ask the trainer for help in case.

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~


!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Create FPM Docker Image

* Objective:
 * Create Dockerfile which provides fpm Ruby gem
* Steps:
 * Open the GitLab project `docker-fpm` details and enter the Web IDE
 * Add a new file, type `Dockerfile`
 * Go to https://github.com/jordansissel/fpm and copy the content of the `Dockerfile`
 * Stage & commit the new Dockerfile to GitLab


~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Create FPM Docker Image

****

Follow the instructions and ask the trainer for help in case.

Dockerfile:

    FROM alpine:3.7

    RUN apk add --no-cache \
            ruby \
            ruby-dev \
            gcc \
            libffi-dev \
            make \
            libc-dev \
            rpm \
        && gem install --no-ri --no-rdoc fpm


~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Use CI to build and push Docker Image

* Objective:
 * Create CI configuration for Docker Image Builds
* Steps:
 * Open the project details and click on `Setup CI / CD`
 * Select the `Docker` template (fallback: https://docs.gitlab.com/ee/ci/examples/README.html)
 * Add the `variables` section on top, overriding the CI_REGISTRY_IMAGE variable with the local path:
 * Commit the change and inspect the CI pipeline on the right (rocket icon)

.gitlab-ci.yml:

    variables:
        CI_REGISTRY_IMAGE: $CI_REGISTRY/osmc/docker-fpm/fpm:latest

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Use CI to build and push Docker Image

****

Follow the instructions and ask the trainer for help in case.

.gitlab-ci.yml

    variables:
        CI_REGISTRY_IMAGE: $CI_REGISTRY/osmc/docker-fpm/fpm:latest

    # This file is a template, and might need editing before it works on your project.
    build-master:
      # Official docker image.
      image: docker:latest
      stage: build
      services:
        - docker:dind
      before_script:
        - docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD" $CI_REGISTRY
      script:
        - docker build --pull -t "$CI_REGISTRY_IMAGE" .
        - docker push "$CI_REGISTRY_IMAGE"
      only:
        - master

    build:
      # Official docker image.
      image: docker:latest
      stage: build
      services:
        - docker:dind
      before_script:
        - docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD" $CI_REGISTRY
      script:
        - docker build --pull -t "$CI_REGISTRY_IMAGE:$CI_COMMIT_REF_SLUG" .
        - docker push "$CI_REGISTRY_IMAGE:$CI_COMMIT_REF_SLUG"
      except:
        - master



~~~SECTION:handouts~~~


****

~~~ENDSECTION~~~

