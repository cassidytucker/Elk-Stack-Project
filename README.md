# Project1

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

CloudSecurityHW.pdf

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

 filebeat-playbook.yml_

This document contains the following details: filebeat-playbook.yml 
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient in addition to restricting traffic to the network.

What aspect of security do load balancers protect? What is the advantage of a jump box?
-Load balancers help maximize performance by delegating traffic so the servers are not overloaded which can also prevent DDOS attacks. An advantage of a jump box is that it is highly secure.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.

What does Filebeat watch for?
It watches the log files that you specify along with any changes to them and forwards them to Elasticsearch or Logstash for indexing.

What does Metricbeat record?
It records the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.

![image](https://user-images.githubusercontent.com/85799340/122127825-c3312880-ce01-11eb-902f-73143678fc27.png)


### Access Policies

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
My Home Public IP Address
Machines within the network can only be accessed by Jump-Box.

Which machine did you allow to access your ELK VM?
Jump-Box

What was its IP address?
10.0.0.4

A summary of the access policies in place can be found in the table below.

![image](https://user-images.githubusercontent.com/85799340/122127668-8402d780-ce01-11eb-8059-c6321c7890c4.png)

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible?
The playbooks can be deployed to any or all VM’s without having to do each 1 by 1.

The playbook implements the following tasks:

Install docker.io (This installs docker.io)
Install python3-pip (This installs python3-pip)
Install Docker module (This installs docker)
Download and launch a docker elk container
Enable docker service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6
- 10.0.0.8

We have installed the following Beats on these machines:
Filebeat and Metrictbeat

These Beats allow us to collect the following information from each machine:
Filebeat collects log files of changes from specified machines and forwards them to Elasticsearch or Logstash for indexing.
Metricbeat collects metrics and statistics from specified machines and forwards them to Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below: 
Copy the install-elk.yml to /etc/ansible
Update the hosts file to include

[elk]
10.1.0.4 ansible_python_interpreter=/usr/bin/python3

Run the playbook, and navigate to http://23.99.80.187:5601/app/kibana#/home to check that the installation worked as expected.

Answer the following questions to fill in the blanks:

Which file is the playbook? Install-elk.yml

Where do you copy it?_
/etc/ansible/

Which file do you update to make Ansible run the playbook on a specific machine? 
/etc/ansible/hosts

How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
There is a section in the /etc/ansible/host file where you can put each Virtual Machine with a specific group

Which URL do you navigate to in order to check that the ELK server is running?
http://23.99.80.187:5601/app/kibana#/home
