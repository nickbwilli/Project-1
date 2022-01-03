# Project-1---Week-13
This repository includes the Ansible YAML, Bash Scripts, and Network Diagrams created in my DU Cybersecurity Bootcamp Week 13 Project 1.



## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/Network Diagram.png
![image](https://user-images.githubusercontent.com/90221329/147609511-1f6ed6ad-1614-4f8e-8f95-7471bbe43344.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML files may be used to install only certain pieces of it, such as Filebeat.

In the Ansible Directory:
- Ansible/Config-DVWA-Docker.txt
- Ansible/ELK-Playbook.txt
- Ansible/filebeat-config.yml
- 

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
Load Balancers increase the availability of the application by routing traffic to two servers. 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.
- Filebeat monitors log data files for activity on the server.
- Metricbeat helps monitor the server metrics from the operating system and services. 

The configuration details of each machine may be found below.

| Name     | Function           | IP Address | Operating System |
|----------|--------------------|------------|------------------|
| Jump Box | Gateway            | 10.0.0.5   | Linux            |
| DVWA1    | Application Server | 10.0.0.6   | Linux            |
| DVWA2    | Application Server | 10.0.0.7   | Linux            |
| ElkVM    | Elk-Stack          | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box and ElkVM machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My Home IPv4 Address

Machines within the network can only be accessed by the Jump Box.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Home IP Address      |
| DVWA1    | No                  | 10.0.0.5             |
| DVWA2    | No                  | 10.0.0.5             |
| ElkVM    | Yes                 | Home IP Address      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows multiple machines/servers to be configured at one time and creates a consistent configuration for all machines.

The playbook implements the following tasks:
- Config Web VM with Docker
	- Install docker.io
	- Install python3-pip
	- Install Python Docker Module
	- Download and Launch the DVWA Container
	- Run the Docker service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/90221329/147987854-f8046778-7e58-4db5-8dc9-d13fd5bb0fb4.png)


### Target Machines & Beats

This ELK server is configured to monitor the following machines:

- DVWA1: 10.0.0.6
- DVWA2: 10.0.0.7

We have installed the following Beats on these machines:

- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects data about the file system.
- Metricbeat collects machine metrics, such as up time.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the 'ELK-Playbook.yml' file to '/etc/ansible' in the container.
- Update the '/etc/ansible/hosts' file to include the ELK stack VM IP address.
- Run the playbook, and navigate to "http://[your.elk.ip]:5601/app/kibana" to check that the installation worked as expected.
