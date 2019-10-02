!SLIDE smbullets
# Merge Requests

* Developer does not have push access to master branch
* Merge Request from branch gets created
* MR is similar to an issue, unique identifier, description, etc.
* MR requires a review
* Maintainer merges MR to master, prepares next release


~~~SECTION:handouts~~~

****


~~~ENDSECTION~~~

!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Create Merge Request

* Objective:
 * Create Merge Request from branch `feature/docs`
* Steps:
 * Either inspect the push message in the terminal
 * Or navigate to `Repository > Branches`
 * Create a merge request from URL/Button
 * Add title, description
 * Milestone: `1.0.0`
 * Tick `Delete source branch when merge request is accepted.`
 * `Submit Merge Request`

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Create Merge Request

****

Follow the instructions and ask the trainer for help in case.

    @@@ Sh
    $ git push -u origin feature/docs
    ...
    remote:
    remote: To create a merge request for feature/docs, visit:
    remote:   https://4014-gitlab-b1d71-web.nws.netways.de/osmc/workshop/merge_requests/new?merge_request%5Bsource_branch%5D=feature%2Fdocs
    remote:
    To https://4014-gitlab-b1d71-web.nws.netways.de/osmc/workshop
     * [new branch]      feature/docs -> feature/docs
    Branch 'feature/docs' set up to track remote branch 'feature/docs' from 'origin'.



~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~



!SLIDE smbullets
# Merge Requests need a Review

* Features need documentation
* Every test case and scenario is handled
* Fully resolves a feature
* Automated CI tests worked
* Merge Request Approvals are Enterprise only
  * https://gitlab.com/gitlab-org/gitlab/issues/20696
  * Use workarounds with "likes" in CE

~~~SECTION:handouts~~~

****


~~~ENDSECTION~~~

!SLIDE smbullets
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Review and Merge MR

* Objective:
 * Review and Merge MR
* Steps:
 * Navigate into `Merge Requests` and select the previously created MR
 * Like the MR
 * Add a comment with `:heavy_check_mark:`
 * Click on `Merge`
 * Verify that the source branch is deleted

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE supplemental solutions
# Lab ~~~SECTION:MAJOR~~~.~~~SECTION:MINOR~~~: Proposed Solution
****

## Review and Merge MR

****

Follow the instructions and ask the trainer for help in case.

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~
