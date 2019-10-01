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
