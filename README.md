# Vagrant Project with Ansible

This repository contains a simple example of a virtual machine which is created via Vagrant and provisioned via Ansible. On start up, we use a base role to set vim as default editor. Using Ansible, you can install docker engine while the VM is running.

In order to use the vagrant file, you have to follow those steps:

- Download and Install [VMware](https://customerconnect.vmware.com/en/downloads/info/slug/desktop_end_user_computing/vmware_workstation_player/17_0) (For Apple silicon) or HyperV
- Download and Install [Vagrant](https://developer.hashicorp.com/vagrant/install)
- Install [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html)
- Open a shell prompt on the root of the project and run `cd vagrant` and `vagrant up` to set up the vm

Vagrant automatically creates an Ansible inventory file in `.vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory`. This inventory is configured according to the SSH tunnel that Vagrant automatically creates.

## Install docker engine on VM

- In order to apply the `docker.yml` playbook on the vm run `cd ansible` and  `ansible-playbook -i ../vagrant/.vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory playbooks/docker.yml`.

## Useful commands

While on the `vagrant` directort you can run:

- `vagrant global-status` to check the status of the VM
- `vagrant ssh test-node` to ssh into the VM
- `vagrant destroy -f` to destroy the VM
