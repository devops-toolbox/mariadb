Role Name
=========

mariadb: Mariadb

[![Build Status](https://travis-ci.org/cmihai-ansible/mariadb.svg?branch=master)](https://travis-ci.org/cmihai-ansible/mariadb)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.mariadb](https://galaxy.ansible.com/devops-toolbox.mariadb)

```bash
ansible-galaxy install devops-toolbox.mariadb
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
mariadb_packages_state: present
mariadb_remove_packages: true
mariadb_enable_service: true
mariadb_enable_selinux: true
mariadb_copy_templates: true
mariadb_firewall_configure: true
mariadb_firewall_rules:
  - service: ssh
  - port: 3389
mariadb_users:
  - user: devops
    group: docker
mariadb_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install mariadb on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: mariadb is configured
      import_role:
        name: devops-toolbox.mariadb
      vars:
        mariadb_packages_state: present
        mariadb_remove_packages: true
        mariadb_enable_service: true
        mariadb_enable_selinux: true
        mariadb_copy_templates: true
        mariadb_firewall_configure: true
        mariadb_firewall_rules:
          - service: ssh
          - port: 3389
        mariadb_users:
          - user: devops
            group: docker
        mariadb_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: mariadb
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
