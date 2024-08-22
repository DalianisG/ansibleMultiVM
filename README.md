# Vagrant Project with Ansible

This repository contains a simple example of a multi-VM setup using Vagrant and Ansible. The project creates four virtual machines (VMs) via Vagrant, which are provisioned using Ansible. On startup, a base role sets `vim` as the default editor. You can also install Docker Engine on the VMs while they are running using Ansible.

## Prerequisites

Ensure you have the following tools installed before using this project:

- Download and Install [VMware](https://customerconnect.vmware.com/en/downloads/info/slug/desktop_end_user_computing/vmware_workstation_player/17_0) (For Apple silicon) or HyperV
- Download and Install [Vagrant](https://developer.hashicorp.com/vagrant/install)
- Install [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html)

## Usage

1. Clone the repository and navigate to the project root.
2. Open a terminal and run the following commands:

``` bash
   cd vagrant
   vagrant up
```

This will set up all the VMs. To set up a specific VM, use:

`vagrant up [vm-name]`

To access a VM via SSH, run:

`vagrant ssh [vm-name]`

Vagrant automatically creates an Ansible inventory file in `.vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory`. This inventory is configured according to the SSH tunnel created by Vagrant.



## Applying Ansible Playbooks

### Set vim as the Default Editor

To apply the `base.yml` playbook, which sets vim as the default editor, run:

``` bash
cd ansible
ansible-playbook playbooks/base.yml
```

### Install Docker Engine on VM

To install Docker Engine on the VMs, run:

``` bash
cd ansible
ansible-playbook playbooks/docker.yml
```

## Troubleshooting

### Known Issues

Occasionally, an error occurs during the booting process. This is an ongoing issue that I am working on fixing. If you encounter this error, try running again the following command:

`vagrant up`

## Useful commands

While on the `vagrant` directort you can run:

- `vagrant global-status`: Check the status of all VMs.
- `vagrant ssh [vm-name]`: SSH into a specific VM.
- `vagrant destroy [vm-name]`: Destroy a specific VM.
- `vagrant destroy -f`: Force destroy all VMs.
