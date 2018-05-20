Nuran Litecell Yocto Build Environment
======================================

This directory contains scripts to generate a self-contained build
environment in a virtual machine to build the Nuran Wireless Litecell
1.5. This automates the initial setup and environment steps detailed
here: https://gitlab.com/nrw_noa/lc15-bts-release-manifest/wikis/home

Requirements
------------

* A working virtualbox install. See https://www.virtualbox.org/
* Vagrant https://www.vagrantup.com/downloads.html
* Ansible http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html
* The vagrant disksize plugin `vagrant plugin install vagrant-disksize

SSH
---

The Nuran download scripts require ssh access to gitlab to
operate. You must create an account on gitlab.com and enable SSH key
access by uploading a valid public key file for your system. To use
SSH from within the virtual machine, you must setup a local ssh-agent,
which will be automatically forwarded to the guest OS by vagrant
(recommended), or manually copy your SSH private key into the virtual
machine (not recommended).

Usage
-----

After installing the above requirements and setting up SSH, simply run
`vagrant up yocto` to generate the build environment. Users will still
need to follow the instructions proved by Nuran at
https://gitlab.com/nrw_noa/lc15-bts-release-manifest/wikis/home to
download the mainfest file and complete their desired build.

Notes
-----

It's important to note that this is a large virtual machine. You may
need to adjust the resources in the vagrantfile if your machine is
relatively lightly resourced.

