!SLIDE smbullets
# Branches

* Naming Schema
  * Use namespaces as prefix
  * `feature/mysql-backend` or `bugfix/daemon-crash`
* Release branches
  * `release/1.0.0`
* Support branches to support older stable releases
  * `support/2.11`


~~~SECTION:handouts~~~

****


~~~ENDSECTION~~~

!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Create and push a new branch

* Objective:
 * Create branch `feature/docs` and push it
* Steps:
 * Use `git checkout -b feature/docs`
 * Edit `README.md` and add `## Workshop Notes` at the bottom
 * Add and commit the changes
 * Push & create the branch remote with `git push -u origin feature/docs`
 * Navigate to `Repository > Branches` in your GitLab project

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Create and push a new branch

****

Follow the instructions and ask the trainer for help in case.

    @@@ Sh
    $ cd $HOME/workshop
    $ git checkout master
    $ git checkout -b feature/docs
    $ vim README.md

    # workshop

    OSMC Workshop

    ## Workshop Notes

    ESC :wq

    $ git add README.md
    $ git commit -v -m "Add notes to docs"

    $ git push -u origin feature/docs

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

