# vagrant-kube

The idea is to create a Kubernetes cluster and provision it with Ansible by using the official kubeadm method.

## Requirements

* Ansible
* Vagrant

## Steps

* Clone this repo
* Deploy VMs by using: `vagrant up`
* Run the Ansible playbook: `ansible-playbook -i inventory.ini site.yml`

## Notes

* This is still a work in progress.

## TODO

* Fetch master's IP address as an Ansible variable
* Use the Vagrant-Ansible provisioner for deploying the cluster in a single run 