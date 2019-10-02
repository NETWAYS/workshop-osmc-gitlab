!SLIDE smbullets
# Exclude files with .gitignore

* Build directories from source code compilation (e.g. `debug`, `release`)
* Files generated at runtime (e.g. test results or stats)
* User specific IDE settings
* Local Vagrant boxes and other temporary files

~~~SECTION:handouts~~~

****

You can use wildcard pattern matches for files.
If you'll end the string with a '/' git will only
ignore directories instead of both directories and files
matching the pattern.

If you want to ignore a file globally in your repository
you can preceed the path with `**/` which means `any directory`.

Example for ignoring a debug file anywhere in your repository:

    **/debug

If you prefer to keep `.gitignore` files in specific directories
and not a global file, this will also work.

~~~ENDSECTION~~~


!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Add .gitignore file and exclude files/directories

* Objective:
 * Add .gitignore file and exclude files/directories
* Steps:
 * Navigate to `Project > Details` and open the Web IDE
 * Add a new file and choose `.gitignore`
 * Select `Go` from the template dropdown
 * Stage and commit the change directly to master

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Add .gitignore file and exclude files/directories

****

Follow the instructions and ask the trainer for help in case.

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~
