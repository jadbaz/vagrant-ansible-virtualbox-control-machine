# Vagrantfile to create an Ansible control machine

## Details
* Starts from the [centos/7 Vagrant image](https://app.vagrantup.com/centos/boxes/7)
* Uses Virtualbox provider with port forwarding
* Syncs the folder it is in with /home/vagrant/ansible

## Usage
* `vagrant up`
* `vagrant ssh`
