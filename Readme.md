# k8s-playbook

Minimal ansible playbook for setting up kubeadm based multi node k8s cluster using VirtualBox VMs as nodes.

## Meant For

Strictly local use for doing POCs or Learning how to setup a multi node k8s cluster from scratch, **Not meant for prod use**. Good for doing spikes / testing upgrades of k8s from one version to another.

## Features

* VagrantFile to setup desired number of networked VirtualBox VMs.
* Easily configurable resource allocation for master and worker nodes.
* Extensible to add multiple worker nodes if you have the hardware capacity. ( default 1 )
* It takes just two commands. ¯\\\_(ツ)_/¯

## Pre-requisites

* Vagrant, VirtualBox and Ansible Installed on Host.
* Internet connectivity for installation and downloading vagrant basebox ( *1.3 GB* ). **Not an offline k8s setup**

## How to use

Ensure Pre-requisites are met. Then from root of repo.

1. `vagrant up`

Once vagrant has finished setting up the vms. Add your host ssh public key as authorised keys in all VM nodes. ( *required for ansible to ssh* )

2. `ansible-playbook -i inventory.ini site.yml`

Once Ansible play is finished. You will find `kubectl` on master node to manage the cluster.

## Planned Features

* Moving etcd out to a separate node.
* Setup multi master cluster.
