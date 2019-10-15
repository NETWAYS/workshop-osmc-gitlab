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
# Protocol

* HTTPS protocol (write access via oauth tokens)
  * `https://my-gitlab.nws.netways.de/username/repo.git`
* Read/write access via SSH
  * `git@github.com:username/repo.git`
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

* Community Edition (CE), Open Source and free to use
* Enterprise Edition (EE), additional features
  * Multiple LDAP servers, LDAP group import
  * Search backend with Elasticsearch, additional HA capabilities
  * Dependency Scanning, Audit logs
  * Merge Request Review Approvals, Issue Relations
  * Burndown charts
  * Epics, manage group of issues over many projects

https://about.gitlab.com/pricing/self-managed/feature-comparison/
https://about.gitlab.com/install/ce-or-ee/


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


