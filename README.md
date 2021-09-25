# Automated ELK Stack Deployment

The files in this repository was used to configure the network depicted below
![ELK Architecture](https://github.com/LuckyML96/ucb-cybersecurity/blob/main/Images/Elk%20Architecture.PNG?raw=true)

These files have been tested and used to generate a live ELK deployment on Azure. 

# Ansible Playbooks
All Playbooks are located in the ansible folder /Ansible and will apply to the IPs specified in the /etc/ansible/hosts file

## config_playbook.yaml:
This playbook is used to configure the webserver VMs with docker and install containers running DVWA

### How to run

ansible-playbook ansible/config_playbook.yaml

## elk-server-playbook.yaml:
This playbook is used to configure the elk server VM with docker and install the elk container

### How to run

ansible-playbook ansible/elk-server-playbook.yaml

## filebeat-playbook.yaml:
This playbook configures and installs filebeat on the webserver VMs. It will copy the configuration file /Ansible/filebeat-config.yml into the container

### How to run

ansible-playbook ansible/filebeat-playbook.yaml

## metricbeat-playbook.yaml:
This playbook configures and installs metrcibeat on the webserver VMs. It will copy the configuration file /Ansible/metricbeat-config.yml into the container

### How to run

ansible-playbook ansible/filebeat-playbook.yaml

# Topology
The main purpose of this project is to expose a load balanced and monitored instance of DVWA (Damn Vulnerable Web Application)
- have a load balanced application adds redundancy in case one of the server goes down and all helps restrict access to the applications

### Table of the existing VMs on the network

| NAME | FUNCTION | IP ADDRESS | OPERATING SYSTEM |
|------|----------|------------|------------------|
|Jump Box| Gateway|10.1.0.4| Linux|
|Web1|Webserver1/DVWA|10.1.0.5|Linux|
|Web2|Webserver2/DVWA|10.1.0.6|Linux|
|ELK|ELK Server|10.2.0.4|Linux|

### Table of the access policies in place on the network

|NAME|EXPOSED PORTS|ALLOWED IP ADDRESSES|
|----|-------------|--------------------|
|JumpBox|22|Local Work Station IP|
|Web1|22|JumpBox - 10.1.0.4|
|Web1|80|Local Work Station IP|
|Web2|22|JumpBox - 10.1.0.4|
|Web2|80|Local Work Station IP|
|ELK|22|JumpBox - 10.1.0.4|
|ELK|5601|Local Work Station IP|

The Jumpbox is the single point that can access the virtual machines within the virtual network. An ssh-key needs to be set up in order to access the jumpbox virutal machine from your local work station. In addition to the generated ssh-key, access rules are also in place to only allow your personal work station ssh access to the jumpbox. All other virtual machines on the network are not exposed to the public network and can only be accessed by the jumpbox. This means to gain access to the webserver vms (10.1.0.5 & 10.1.0.6), you have to be within the jumpbox with the private ip (10.1.0.4). Similarly the ELK server Virtual Machine can only be accessed via the jumpbox IP.
