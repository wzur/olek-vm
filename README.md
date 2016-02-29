# olek-vm
Provisioning of a CentOS7 virtual machine using Vagrant and Ansible.

Host are provisioned with [Ansible](http://docs.ansible.com). Main Ansible playbook is located in `provisioning/site.yml`

Virtual machine is created with [VirtualBox](https://www.virtualbox.org/)

## Requirements ##
* VirtualBox >= 4.3.26
* Ansible >= 1.9.0
* Vagrant >= 1.7.0

############################
## Additional Vagrant Plugins Installation

### Install Vagrant Hostmanager Plugin
`vagrant plugin install vagrant-hostmanager`

### Start virtual machine
`vagrant up`
