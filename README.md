# Automated ELK Stack Deployment

The files in this repository was used to configure the network depicted below

![ELK Architecture](https://github.com/LuckyML96/ucb-cybersecurity/blob/main/Diagrams/Elk%20Architecture.PNG?raw=true)

These files have been tested and used to generate a live ELK deployment on Azure. 

# Ansible Playbooks
All Playbooks are located in the ansible folder /Ansible

## config_playbook.yaml:
This playbook is used to configure the webserver VMs with docker and install containers running DVWA

### How to run

ansible-playbook ansible/config_playbook.yaml

## elk-server-playbook.yaml:

### How to run

ansible-playbook ansible/elk-server-playbook.yaml

## filebeat-playbook.yaml:

### How to run

ansible-playbook ansible/filebeat-playbook.yaml

## metricbeat-playbook.yaml:

### How to run

ansible-playbook ansible/filebeat-playbook.yaml
