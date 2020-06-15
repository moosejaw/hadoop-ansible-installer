# Ansible Playbook for installing Hadoop
**You will probably need to repoint the download URL for Hadoop in the Playbook. During testing it seems to routinely move and therefore break.**

This is an Ansible Playbook for downloading and installing Apache Hadoop 3.1.2. It is an install for the CT6045 module at the University of Gloucestershire. Don't use it in production.

Use this playbook on Ubuntu or another distribution of Linux which uses the apt package manager. You can adapt the playbook to use the generic package manager commands if you want to.

This repository contains a hosts file for running the script on localhost. You can modify this to distribute the install if you want to.

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

You need to assign a UNIX password to `hduser`. You can do this by running:
```bash
sudo passwd hduser
```

And then entering a UNIX password.

Next, log in as hduser, generate a public key and add it to your authorized_keys
```bash
su - hduser
bash
ssh-keygen -t rsa -P ""
cat /home/hduser/.ssh/id_rsa.pub >> /home/hduser/.ssh/authorized_keys
```

You will then need to restart your machine, then you can start Hadoop as `hduser`.
