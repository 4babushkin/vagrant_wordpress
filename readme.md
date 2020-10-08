# Install Wordpress website running on 2 virtual machines with Vagrant and Ansible. The access to `/wp-admin` is protected by [Online LDAP Test Server](https://www.forumsys.com/tutorials/integration-how-to/ldap/online-ldap-test-server/)

## What must be installed
* vagrant https://www.vagrantup.com/downloads.html
* ansible https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html
* virtualbox https://www.virtualbox.org/wiki/Downloads

## Virtual machines (VM)

dbserver - VM with mysql database

appserver - VM with apache, php and wordpress

## Setting variables

configuration variables in file `/vars/main.yml`

This file can be protected with Ansible Vault.

## Execute

```
vagrant up
```

Wordpress website is available at http://10.10.10.20/

The access to http://10.10.10.20/wp-admin is protected by Online LDAP Test Server


## Description

Two roles and the playbook were written

**common** role is started in all VM and this role preconfigurates them.

**mysql** role is started only in dbserver VM. This role installs and configurates mysql server for Wordpress

I didn't write a role for installing apache. I wrote a playbook /**playboks/wordpress.yml** and imported it to the main playbook **site.yml**. because it is permitted.

## P.S.

when Vagrant is up, one can run Ansible manually
```
vagrant provision
```
However, it is inconvenient while developing ansible playbooks, and one can run
```
ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory site.yml
```