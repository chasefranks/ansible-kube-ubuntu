# Ansible Playbooks to Install Kubernetes on Ubuntu

A collection of Ansible playbooks to setup and initialize a Kubernetes cluster on Ubuntu 16.04 LTS. We basically take the instructions from [Installing Kubernetes on Linux with kubeadm](https://kubernetes.io/docs/getting-started-guides/kubeadm/) and make them available as playbooks.

## Quick Start

To install Docker and Kubernetes

```
ansible-playbook kube-install.yaml
```

To initialize the master node

```
ansible-playbook kubemaster-init.yaml
```

To join nodes

```
ansible-playbook kube-join.yaml
```

## Setting Up Your Inventory

Included in this repo is a sample ansible inventory file. The groups defined are

* kubes - all kubernetes nodes (master + worker nodes)
* kubemaster - the kubernetes master node
* kube-nodes - worker nodes

Change these ip addresses to target your Kubernetes hosts. Then tell ansible where your inventory file is by either setting the ANSIBLE_INVENTORY environment variable

```
export ANSIBLE_INVENTORY=$(pwd)/ansible_inventory
```

or run the ansible-playbook commands above with the -i flag:

```
ansible-playbook -i ./ansible_inventory playbook.yaml
```

To test that ansible can reach your inventory over ssh, run

```
ansible kubes -m ping -u <remote_user>
```
