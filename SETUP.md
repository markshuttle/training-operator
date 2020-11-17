#! /bin/sh

# Install MicroK8s

sudo snap install microk8s --classic
sudo usermod -a -G microk8s $USER
sudo su - $USER
microk8s status --wait-ready
microk8s.enable dns storage

# Install Charmcraft

sudo snap install charmcraft --beta

# Install Juju

sudo snap install juju --classic

# Deploy the operator lifecycle manager

juju bootstrap microk8s micro
juju add-model training

# https://juju.is/docs/microk8s-cloud
