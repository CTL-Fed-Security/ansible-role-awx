# Ansible Role: AWX (open source Ansible Tower)

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-awx.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-awx)

Installs and configures [AWX](https://github.com/ansible/awx), the open source version of [Ansible Tower](https://www.ansible.com/tower).

## Requirements

Before this role runs, you need to make sure the following AWX dependencies are installed:

| Dependency                    | Suggested Role           |
| ----------------------------- | ------------------------ |
| EPEL repo (RedHat OSes only)  | `geerlingguy.repo-epel`  |
| Git                           | `geerlingguy.git`        |
| Ansible                       | `geerlingguy.ansible`    |
| Docker                        | `geerlingguy.docker`     |
| Python Pip                    | `geerlingguy.pip`        |
| Node.js (6.x)                 | `geerlingguy.nodejs`     |

See this role's `tests/test.yml` playbook for an example that works across many different OSes.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    awx_repo: https://github.com/ansible/awx.git
    awx_repo_dir: "~/awx/"
    awx_version: devel
    awx_keep_updated: yes

Variables to control what version of AWX is checked out and installed.

## Dependencies

None.

## Example Playbook

    - hosts: awx-centos
      become: yes
    
      vars:
        nodejs_version: "6.x"
        pip_install_packages:
          - name: docker-py
    
      roles:
        - geerlingguy.repo-epel
        - geerlingguy.git
        - geerlingguy.ansible
        - geerlingguy.docker
        - geerlingguy.pip
        - geerlingguy.nodejs
        - role_under_test

## License

MIT / BSD

## Author Information

This role was created in 2017 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).