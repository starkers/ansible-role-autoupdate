Autoupdates
===========

Enable automatic updating on an Ubuntu or CentOS server. This simply installed and activates either yum-cron or cron-apt and attempts to configure them.

They (should) default to daily checks and updates.

Should work OK on most Distro's although I've not made it too generic as I've not had the time to test yet.

Requirements
------------

- apt or yum (tested on Ubuntu 14.04 + Centos 6)
- The target server should have access to updates
- Email should work so you can get notifications

Role Variables
--------------

There are currently only a few

 - autoupdate_enable: **no** or **yes** (default: yes)
 - autoupdate_notifyonly: **no** or **yes** (default: no)
 **NOTE** this only works on centos
 - autoupdate_email: your@address.com (default: root)

 With these simple variables there are several options now..


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

License
-------

BSD

Author Information
------------------

david@starkers.org
