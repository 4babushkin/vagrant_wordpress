
# Install Wordpress website running on 2 virtual machines with Vagrant and Ansible. The acces to `/wp-admin` protected by [Online LDAP Test Server](https://www.forumsys.com/tutorials/integration-how-to/ldap/online-ldap-test-server/)

## What needs to be installed
* vagrant https://www.vagrantup.com/downloads.html
* ansible https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html
* virtualbox https://www.virtualbox.org/wiki/Downloads


dbserver - instanse with mysql database

appserver - instanse with apache, php and wordpress

## Setting variables



## Execute

```
vagrant up
```

Wordpress website is available at http://10.10.10.20/

The acces to http://10.10.10.20/wp-admin protected by Online LDAP Test Server


## P.S.

If you want to run Ansible manually 
```
ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory site.yml
```