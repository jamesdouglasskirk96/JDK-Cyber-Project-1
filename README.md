# JDK-Cyber-Project-1
Cyber Class Project 1

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/jamesdouglasskirk96/JDK-Cyber-Project-1/blob/main/Diagrams/Red-Team-Network-Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the configuration file may be used to install only certain pieces of it, such as Filebeat.

https://github.com/jamesdouglasskirk96/JDK-Cyber-Project-1/blob/main/Ansible/elk.md

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

The Jump Box is the center of the network. This is where administrators connect to the network resources via a secure SSH connection without needing to directly connect to the resources in the network

Load balancing ensures that the application will be highly scalable, in addition load balancers help prevent DDoS attacks on the network. The Load Balancer can be seen as a preventitive measure that keeps unwanted people out with assistance from the Firewall and also ensures that everyone that should be able to access the application has access.  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the security group and system configuration.
- Filebaet: ELK stack tool for log file analysis
- Metricbeat: ELK stack tool for visuals of the data on the server. Comes with clean UI interface

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Server   | 10.0.0.5   | Linux            |
| Web-2    | Server   | 10.0.0.6   | Linux            |
| Web-3    | Server   | 10.0.0.8   | Linux            |
| Elk-Stack| Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 68.203.2.136

Machines within the network can only be accessed by SSH

The Jump Box can also access the ELK stack server via its private IP. ( 10.0.0.4 )

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 68.203.2.136         |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| Web-3    | No                  | 10.0.0.4             |
| Elk-Stack| No                  | 10.0.0.4             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

Ansible allows CI/CD ( Continuious Integration & Continuous Deployment ). Playbook files allows automated deployment of containers on demand without having to manually type commands.  

The playbook implements the following tasks:

- Install Docker.io
- Install pip3
- Install Docker Python module
- Download and launch a docker web container
- Enable docker service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/jamesdouglasskirk96/JDK-Cyber-Project-1/blob/main/Diagrams/Docker_ps_output.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

- Web-1 10.0.0.5
- Web-2 10.0.0.6
- Web-3 10.0.0.8


We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
Filebeat allows us to easily collect and analyze log data. This service monitors log files and other specified directories, collects events, and forwards them to Elasticsearch or Logstash for indexing and visualizing the data. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk.yml file to /etc/ansible.
- Update the elk.yml file to include the appropriate IP addresses
- Run the playbook, and navigate to http://52.143.96.181:5601/app/kibana to check that the installation worked as expected. ( The IP mentioned is specific to the ELK server in the resource group )
