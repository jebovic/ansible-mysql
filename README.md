yamlMySQL
=====

[![Build Status](https://travis-ci.org/jebovic/ansible-mysql.svg?branch=master)](https://travis-ci.org/jebovic/ansible-mysql) [![Ansible Galaxy](https://img.shields.io/badge/galaxy-jebovic.mysql-blue.svg?style=flat)](https://galaxy.ansible.com/jebovic/mysql)

Install and configure MySQL, add default user and default database

This role is a part of my [OPS project](https://github.com/jebovic/ops), follow this link to see it in action. OPS provides a lot of stuff, like a vagrant file for development VMs, playbooks for roles orchestration, inventory files, examples for roles configuration, ansible configuration file, and many more.

Compatibility
-------------

Tested and approved on :

* Debian jessie (8+)
* Ubuntu Trusty (14.04 LTS)
* Ubuntu Xenial (16.04 LTS)

Role Variables
--------------

```yaml
# Mysql basic configuration
mysql_port: 3306
mysql_user: mysql
mysql_pid_file: /var/run/mysqld/mysqld.pid
mysql_base_dir: /usr
mysql_data_dir: /var/lib/mysql
mysql_tmp_dir: /tmp
mysql_bind_address: 127.0.0.1
mysql_error_log_file: /var/log/mysql/error.log

# Create default database
default_database_enabled: yes
default_database_name: default_db
default_database_encoding: utf8
default_database_collation: utf8_general_ci
default_database_state: present

# Create default user
default_user_enabled: yes
default_user_name: db_user
default_user_password: db_user
default_user_host: localhost
default_user_priv: "{{ default_database_name }}.*:ALL"
default_user_state: present

```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
     - { role: jebovic.mysql }
```

Example : config
----------------

```yaml
# Do not create default database
default_database_enabled: no
# Do not create default user
default_user_enabled: no
#  Bind server ip, not only localhost
mysql_bind_address: "{{ ansible_host }}"
```

Tags
----

* mysql_config : only update config and restart service

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic
