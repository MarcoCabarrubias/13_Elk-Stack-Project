# 13_Elk-Stack-Project
Project Submission for Week 13

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!https://github.com/MarcoCabarrubias/13_Elk-Stack-Project/blob/main/Diagrams/Network%20Diagram.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - elk-intall.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
 - Load Balancers protect the network from DDoS attacks by distributing traffic to different web servers and ensuring that no single server becomes overworked.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
 - Filebeat monitor the log files or location that you specify, collects log events and forwards them either to Elasticsearch or Logstash for indexing.
 - Metricbeat records the metric and statistics from the system and services it is running.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name         | Function     | IP Address | Operating System |
|--------------|--------------|------------|------------------|
| JumpBoxAdmin | Gateway      | 10.0.0.4   | Ubuntu           |
| Web-1        | Web Server 1 | 10.0.0.5   | Ubuntu           |
| Web-2        | Web Server 2 | 10.0.0.7   | Ubuntu           |
| ELK-Server   | ELK Server   | 10.1.0.4   | Ubuntu           |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 
Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
 - 10.0.0.4

Machines within the network can only be accessed by .
 - Web-1
 - Web-2

A summary of the access policies in place can be found in the table below.

| Name         | Publicly Accessible | Allowed IP Addresses |
|--------------|---------------------|----------------------|
| JumpBoxAdmin | Yes                 | 10.0.0.4             |
| Web-1        | No                  |                      |
| Web-2        | No                  |                      |
| ELK-Server   | No                  |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
 - the ansible will automatically restart everytime we log in.

The playbook implements the following tasks:
 - download docker image
 - install python
 - use more memory
 - download and launch a docker elk container
 - enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/MarcoCabarrubias/13_Elk-Stack-Project/blob/main/Diagrams/docker_ps.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
 - 10.0.0.5
 - 10.0.0.7

We have installed the following Beats on these machines:
 - filebeats
 - metricbeats

These Beats allow us to collect the following information from each machine:
 - Filebeat monitor the log files or location that you specify, collects log events and forwards them either to Elasticsearch or Logstash for indexing.
 - Metricbeat records the metric and statistics from the system and services it is running.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?
	- playbook.yml (i.e filebeat-playbook.yml)
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
	- config.yml (i.e filebeat-config.yml), you can specify which achine to install it on by adding the IP Adressess of the machine/s.
- _Which URL do you navigate to in order to check that the ELK server is running?
	- http://"localhost":5601 - where localhost is the IP Address of the elk server.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._