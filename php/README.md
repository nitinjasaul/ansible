Role Name
=========

Role to install different versions of PHP on Ubuntu/CentOS.

Requirements
------------

Python must be installed on the node machine.

Role Variables
--------------

Epel repository URLs -

epel_repo_url: "https://dl.fedoraproject.org/pub/epel/epel-release-latest-{{ ansible_distribution_major_version }}.noarch.rpm"
epel_repo_gpg_key_url: "/etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-{{ ansible_distribution_major_version }}"
epel_repofile_path: "/etc/yum.repos.d/epel.repo"

variables in vars/main.yml

# For CentOS give version=55 or 56 or 70 in extra vars 
php_centos:
  - php{{ version }}w
  - php{{ version }}w-opcache
  - php{{ version }}w-xml
  - php{{ version }}w-mcrypt
  - php{{ version }}w-gd
  - php{{ version }}w-devel
  - php{{ version }}w-mysql
  - php{{ version }}w-intl
  - php{{ version }}w-mbstring
  - php{{ version }}w-bcmath

# For Ubuntu give version=5.5 or 5.6 or 7.0 in extra vars 
php_ubuntu:
  - php{{ version }}
  - php{{ version }}-mcrypt
  - php{{ version }}-mysql
  - php{{ version }}-curl
  - php{{ version }}-json
  - php{{ version }}-cgi


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: centos or ubuntu
      roles:
         - { role: php }
         
How to run the Playbook
-----------------------

- For CentOS

ansible-playbook -i hosts(your host file) site.yml --extra-vars version=55/56/70 or 71

- For Ubuntu

ansible-playbook -i hosts(your host file) site.yml --extra-vars version=5.5/5.6/7.0 or 7.1

License
-------

BSD

Author Information
------------------

http://opstree.com
