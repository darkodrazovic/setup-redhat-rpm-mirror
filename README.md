Setup Red Hat RPM mirror
=========

Ansible role for the local Red Hat mirror setup, it covers:
- RedHat 7
- RedHat 8

It will create a daily crontab script for the RPM sync, install required packages, and set up SELinux.

Requirements
------------

Ansible server:
- Ansible 2.7+

Target machine(s):
- SSH connection and root (or sudo) access
- Internet access
- Machine is already registered and subscribed to Red Hat
- Package repositories are already configured and in use
- And most important - enough free disk space for the RPM sync (default 100GB)

Role Variables
--------------

File: defaults/main.yml
  - redhat_8_repo_path (default: /var/www/html/repo)
  - redhat_8_repos (default: rhel-8-for-x86_64-appstream-rpm, rhel-8-for-x86_64-baseos-rpm)
  - redhat_7_repo_path (default: /var/www/html/repo)
  - redhat_7_repos (default: rhel-7-server-rpms, rhel-7-server-optional-rpms)

Dependencies
------------

Enough of free disk space on path defined under defaults/main.yml:redhat_X_repo_path


Example Playbook
----------------
Install the role

Playbook example

    - name: Setup local Red Hat RPM mirror
      hosts: all
      become: yes
      become_user: root
      become_method: sudo
      gather_facts: true
      ignore_errors: no
    
      roles:
         - setup-redhat-rpm-mirror


Author Information
------------------

Darko Drazovic \
LinkedIn: https://www.linkedin.com/in/darkodrazovic \
Personal: https://darkodrazovic.in.rs \
Blog: https://kompjuteras.com \
GitHub: https://github.com/darkodrazovic
