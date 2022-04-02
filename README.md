# Homework
A repository for my homework
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Homework/Diagrams/ElkStackDiagram.drawio]

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - Homework/Ansible/filebeat-playbook.yml
  - Homework/Ansible/metricbeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.

Load balancers distribute the traffic over the available servers. It helps keep the application available because it doesn't rely on either server on its own to keep the application running. 


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system services.


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
| Web 1    |  Server  | 10.1.0.7   | Linux            |
| Web 2    |  Server  | 10.1.0.8   | Linux            |
| Elk-Serv |  Server  | 10.0.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 209.237.96.2


Machines within the network can only be accessed by Jumpbox.
209.237.96.2 can access ELK-Server

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 209.237.96.2         |
| Web-1    | No                  |  	10.1.0.4          |
| Web-2    | No                  |    10.1.0.4          |
| ELK-Serv | No                  |    10.1.0.4          |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it saves time and keeps all settings the same on all machines that run the playbook file.


The playbook implements the following tasks:
* Configure Elk VM with docker
* Install Docker.io
* Install Pip3
* Install Docker python module
* Download and launch a docker elk container


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| Name     | IP Addresses |
|----------|--------------|
| Web 1    | 10.1.0.7     |
| Web 2    | 10.1.0.8     |

We have installed the following Beats on these machines:
Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat- examines and displays log information
Metricbeat- collects metrics from the OS and the services that are running.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to the control node.
- Update the hosts file to include webservers and elk
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_

filebeat-playbook.yml  -> jumpbox -> ansible container      -> /etc/ansible/files

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?

The hosts file. change the value under hosts in the yml file to the group name of the machines you want to download filebeat on. 

- _Which URL do you navigate to in order to check that the ELK server is running?

http://20.114.18.16:5601/app/kibana
