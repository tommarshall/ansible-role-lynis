Ansible Role: Lynis
=========

[![Build Status](https://travis-ci.org/tommarshall/ansible-role-lynis.svg?branch=master)](https://travis-ci.org/tommarshall/ansible-role-lynis)

Installs the [Lynis](https://cisofy.com/lynis/) security auditing tool on RHEL/CentOS or Debian/Ubuntu servers.

Requirements
------------

None.

Role Variables
--------------

```yml
lynis_version: 2.5.8
lynis_version_sha256sum: cb18e95e83c414ab36b125c9aa97c9a79b10a7cba2e94e622242611af5042ffb
```
The version and corresponding `sha256sum` of Lynis to install. Latest version and hash can be found on the [Lynis download page](https://cisofy.com/download/lynis/).

```yml
lynis_src_directory: /usr/local/src/
```
The directory to store the `.tar.gz` and Lynis src files.

```yml
lynis_dest_directory: /opt
```
The directory to hold the Lynis installation.

```yml
lynis_log_directory: /var/log/lynis
```
The directory for the Lynis logs. Used by the cron job. By default Lynis will output the report to `stdout` and log to `/var/log/lynis.log` and `/var/log/lynis-report.dat`.

```yml
lynis_cron: yes
lynis_cron_weekday: "*"
lynis_cron_hour: 3
lynis_cron_minute: 30
```
Lynis cron job configuration. The report, report log, and report data are all written to the `lynis_log_directory`.

Dependencies
------------

None.

Example Playbook
----------------

```yml
- hosts: all
  roles:
     - { role: tommarshall.lynis, tags: [lynis] }
```

License
-------

MIT / BSD
