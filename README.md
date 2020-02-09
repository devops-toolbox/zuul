Role Name
=========

zuul: Zuul

[![Build Status](https://travis-ci.org/cmihai-ansible/zuul.svg?branch=master)](https://travis-ci.org/cmihai-ansible/zuul)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.zuul](https://galaxy.ansible.com/devops-toolbox.zuul)

```bash
ansible-galaxy install devops-toolbox.zuul
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
zuul_packages_state: present
zuul_remove_packages: true
zuul_enable_service: true
zuul_enable_selinux: true
zuul_copy_templates: true
zuul_firewall_configure: true
zuul_firewall_rules:
  - service: ssh
  - port: 3389
zuul_users:
  - user: devops
    group: docker
zuul_selinux_booleans:
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
- name: Install zuul on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: zuul is configured
      import_role:
        name: devops-toolbox.zuul
      vars:
        zuul_packages_state: present
        zuul_remove_packages: true
        zuul_enable_service: true
        zuul_enable_selinux: true
        zuul_copy_templates: true
        zuul_firewall_configure: true
        zuul_firewall_rules:
          - service: ssh
          - port: 3389
        zuul_users:
          - user: devops
            group: docker
        zuul_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: zuul
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
