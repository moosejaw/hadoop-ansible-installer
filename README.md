# Ansible Playbook for installing Hadoop
This is an Ansible Playbook for downloading and installing Apache Hadoop. It is a minimal install for the CT6045 module at the University of Gloucestershire. Don't use it in production.

Use this playbook on Ubuntu or another distribution of Linux which uses the apt package manager. You can adapt the playbook to use the generic package manager commands if you wish.

This repository contains a hosts file for the purpose of running the script on localhost. You can modify this to distribute the install if you wish.

## Running the Playbook
You first need to get Ansible on your system. Assuming you're using a distro with the `apt` package manager, run:
```bash
sudo apt-get update
sudo apt-get install ansible
```

This automatically installs the `ansible-playbook` binary for you. It is automatically added to `PATH`.

Next, clone this repository and set your working directory to the project folder.
From there, run:
```bash
sudo ansible-playbook -i hosts -vv main.yml
```

It should then automatically install Hadoop for you.

You will then need to restart your machine, then you can start Hadoop as `hduser`.
