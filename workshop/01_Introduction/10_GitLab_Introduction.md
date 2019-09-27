!SLIDE smbullets
# GitLab Server

* Central storage for repositories
* Collaboration between teams
* User based access control
* Trigger events (e.g. for CI)

~~~SECTION:handouts~~~

****

In case you don't want to host your own GitLab server,
there are open source and enterprise hosting options available.

NETWAYS also provides GitLab hosting services:

* https://www.netways.de/managed_hosting/gitlab_ce_hosting/
* https://nws.netways.de/products/gitlab-ce

~~~ENDSECTION~~~
!SLIDE smbullets
# Server Overview

* Git server daemon
* Web interface
* Entire collaboration suites
  * GitHub
  * GitLab
  * Bitbucket


~~~SECTION:handouts~~~

****


~~~ENDSECTION~~~

!SLIDE smbullets noprint
# GitLab

<center><img src="../../_images/server/git_server_gitlab.png" style="width: 800px;" alt="GitLab"/></center>

!SLIDE smbullets printonly
# GitLab

<center><img src="../../_images/server/git_server_gitlab.png" style="width:450px" alt="GitLab"/></center>
!SLIDE smbullets noprint
# GitHub

<center><img src="../../_images/server/git_server_github.png" style="width: 800px;" alt="GitHub"/></center>

!SLIDE smbullets printonly
# GitHub

<center><img src="../../_images/server/git_server_github.png" style="width:450px" alt="GitHub"/></center>


!SLIDE smbullets
# Server Protocol

* Read/write access via SSH
  * `git@github.com:username/repo.git`
* HTTPS protocol (write access via oauth tokens)
  * `https://my-gitlab.nws.netways.de/username/repo.git`
* Git protocol
  * `git://domain.com/repo.git`
* Local protocol
  * `file:///opt/git/repo.git`


!SLIDE smbullets
# GitLab Overview

GitLab is available as self-hosted or cloud based repository management
system.

* Git repositories
* User and group management and fine granular permissions
* Issue tracking and project management (dashboards, etc.)
* Merge, review, report
* Continuous integration/deployment (CI/CD)

Hosted: https://www.netways.de/managed_hosting/gitlab_ce_hosting/

NWS: https://nws.netways.de/products/gitlab-ce

~~~SECTION:handouts~~~

****

~~~ENDSECTION~~~

!SLIDE smbullets
# GitLab Editions

* Community Edition (CE), part of this training
* Enterprise Edition (EE), additional features
  * Multiple LDAP servers
  * LDAP group import
  * Merge Request Review Approvals
  * Git Hooks (not web hooks)
  * Search backend with Elasticsearch



~~~SECTION:handouts~~~

****

Overview: https://about.gitlab.com/features/
Comparison: https://about.gitlab.com/images/feature_page/gitlab-features.pdf

The source code is publicly available for both editions.
You'll need a valid license for running EE in production.

~~~ENDSECTION~~~


!SLIDE smbullets
# GitLab Components

* Ruby on Rails application (unicorn, sidekiq)
* Nginx webserver
* PostgreSQL database backend
* Redis cache
* NodeJS for Javascript rendering
* Golang for background daemons

It is recommended to use the Omnibus installation package or use
a managed cloud hosting service.

~~~SECTION:handouts~~~

****


Omnibus packages: https://about.gitlab.com/installation/?version=ce

More details on the manual installation instructions can be
found in the official documentation: https://docs.gitlab.com/ce/install/installation.html

~~~ENDSECTION~~~


