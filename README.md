MySQL
=====

[![Build Status](https://travis-ci.org/jebovic/ansible-mysql.svg?branch=master)](https://travis-ci.org/jebovic/ansible-mysql) [![Ansible Galaxy](https://img.shields.io/badge/galaxy-jebovic.mysql-blue.svg?style=flat)](https://galaxy.ansible.com/jebovic/mysql)

Install and configure MySQL, add default user and default database

Role Variables
--------------

```
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
default_database_name: default_db
default_database_encoding: utf8
default_database_collation: utf8_general_ci
default_database_state: present

# Create default user
default_user_name: db_user
default_user_password: db_user
default_user_host: localhost
default_user_priv: "{{ default_database_name }}.*:ALL"
default_user_state: present
```

Example Playbook
----------------

```
    - hosts: servers
      roles:
         - { role: jebovic.mysql }
```

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic
