nginx-lua-centos7
=================

Build nginx with lua for CentOS7 or RHEL7 

Do not run this as root!

1. Initialize RPM build environment

    ```mkdir -p ~/rpmbuild/{BUILD,RPMS,SOURCES,SPECS,SRPMS}```

    ```echo "%_topdir %(echo $HOME)/rpmbuild" > ~/.rpmmacros```
1. Install nginx source RPM

    ```wget http://nginx.org/packages/rhel/7/SRPMS/nginx-1.6.2-1.el7.ngx.src.rpm```

1. Download additional sources

    ```spectool -g -R nginx-lua.spec```
1. Install stuff for building

    ```yum -y install gcc openssl-devel zlib-devel pcre-devel lua```

1. Install lua-devel, which is not present in standard repos including EPEL for some reason

    ```sudo yum -y install ftp://rpmfind.net/linux/centos/7.0.1406/os/x86_64/Packages/lua-devel-5.1.4-14.el7.x86_64.rpm```
1. ```rpmbuild -ba nginx-lua.spec```


Tested on RHEL 7.0 (Maipo) x86_64

