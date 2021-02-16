# Get started with Ansible using a minimal setup

## Setup a virtual machine
- Install [Vagrant](https://www.vagrantup.com/) on the machine
- [up and run](https://learn.hashicorp.com/tutorials/vagrant/getting-started-index?in=vagrant/getting-started) a virtual machine [using private network](https://www.vagrantup.com/docs/networking/private_network)

## Inventory Setup

Setup the ansible inventory to make the virtual machine as host

```
[webservers]
vagrant-server ansible_host={{IP_ADDRESS} ansible_port=22 ansible_user=vagrant ansible_ssh_private_key_file={{LOCATION_TO_THE_PRIVATE_KEY}
```
> To get the location of the private key of a vagrant virtual machine, please check this [blog](https://lebenplusplus.de/2017/07/19/how-to-use-your-vagrant-box-ssh-credentials/)

## Module


```
$ ansible webservers -m ping
```