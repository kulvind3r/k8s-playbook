# k8s-playbook

Minimal ansible playbook for setting up kubeadm based k8s cluster using VirtualBox vms serving as bare metal servers.

## Meant For

Strictly local usage for doing POCs or Learning how to setup k8s cluster from scratch, **Do not assume this is production level code**. Good for doing spikes / testing upgrades of k8s from one version to another.

## Features

* VagrantFile to setup desired number of networked virtualbox VMs.
* Easily Configurable resource allocation for master and worker nodes.
* Extensible to add multiple worker nodes if you have the Hardware for it. ( default 1 )
* Completely functional k8s cluster setup with Calico CNI from scratch in two commands.

## Pre-requisites

* Vagrant, VirtualBox and Ansible Installed on Host.
* Vagrant Basebox to be provided by the user. Tested with Centos 7.8 minimal basebox.
* Basebox needs vagrant public insecure key and host ssh key as authorized keys and Vagrant user to be part of suoders group. (*Required for ansible's password less sudo needs*).
* Internet connectivity for installation. **This is not an offline setup of k8s**

## How to use

Ensure Pre-requisites are met. ssh keys / vagrant in sudoers / internet connectivity etc. Then from root of repo.

1. `vagrant up`

Once vagrant has finished setting up the vms.

2. `ansible-playbook -i inventory.ini site.yml`

## Planned Features

* Moving etcd out to a separate node.
* Setup multi master cluster.
