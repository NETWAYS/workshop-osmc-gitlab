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

!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Add CI Variables

* Objective:
 * Add CI variable and print it inside the container
* Steps:
 * Navigate to `Project > Details` and open the Web IDE
 * Edit `.gitlab-ci.yml`
 * Add `variables` section
 * Add `BUILD_TYPE: snapshot` as variable
 * Print the variable with `- echo ${BUILD_TYPE}` in the `script` section
 * Stage, commit, merge request, inspect CI job, merge

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Add CI Variables

****

Follow the instructions and ask the trainer for help in case.

    @@@ Sh
    image: centos:7

    variables:
        BUILD_TYPE: snapshot

    all_tests:
        script:
            - echo ${BUILD_TYPE}
            - exit 0



Job output:

    $ echo ${BUILD_TYPE}
    snapshot
    $ exit 0

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~
