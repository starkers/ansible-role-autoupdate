Autoupdates
===========

Enable automatic updating on an Ubuntu or CentOS server. This simply installs and activates either yum-cron or cron-apt and attempts to configure them.

They (should) default to daily checks and updates. If you want to disable updates set '''autoupdate_enable: false'''

Should work OK on most Distro's but I've intentionally made it quite specific to be safe.

Please help me to add support for more environments (EG: debian, centos7) by testing or requesting. -D


Requirements
------------

- apt or yum (tested on Ubuntu 14.04 + Centos 6)
- The target server should have access to updates
- the server should have working email (if you want notifications)

Role Variables
--------------

There are currently only a few

 - autoupdate_enable: **no** or **yes** (default: yes)
 - autoupdate_email: your@address.com (default: root)

**NOTE** I still need to do tests to ensure the email stuff works but for now enabling updates works OK.


Playbook Examples
-----------------
#### default (enable updates)

```
- hosts: servers
  roles:
    - stark.autoupdate
```

#### disable updates
This disables updating via yum-cron / apt-cron (untested really).

```
- hosts: servers
  vars:
  - autoupdate_enable: false
  roles:
    - stark.autoupdate
```

Dependencies
------------

I've only tested this on Ubuntu 14.04 and Centos6


TODO
----

#### I'd like to extend the following features sometimee..
- schedule when they happen
- download updates but don't run
- download and alert me
- alert me but do nothing
- alert me if no updates have been run after XX days
- send a test email to ensure alerting works
- support for more platforms (including freebsd+pcbsd's new pkgng)

License
-------

BSD

Author Information
------------------

david@starkers.org
