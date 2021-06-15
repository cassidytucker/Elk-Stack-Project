# Project1

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![CloudSecurityHW.pdf)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook.yml_

This document contains the following details:filebeat-playbook.yml 
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient in addition to restricting traffic to the network.

- What aspect of security do load balancers protect? What is the advantage of a jump box?
 Load balancers help maximize performance by delegating traffic so the servers are not overloaded which can also prevent DDOS attacks. An advantage of a jump box is that it is highly secure.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.

-What does Filebeat watch for?
It watches the log files that you specify along with any changes to them and forwards them to Elasticsearch or Logstash for indexing.
What does Metricbeat record?
It records the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.


Name	Function	IP Address	Operating System
Jump Box	Gateway	52.188.204.113(Public) 10.0.0.4(Private)	Linux
Web-1	Server	52.249.250.202(Public) 10.0.0.5(Private)	Linux
Web-2	Server	52.249.250.202(Public) 10.0.0.6(Private)	Linux
Web-3	Server	52.249.250.202(Public) 10.0.0.8(Private)	Linux
Elk-VM	Server	52.249.250.202(Public) 10.1.0.4(Private)	Linux![image](https://user-images.githubusercontent.com/85799340/122126784-3df94400-ce00-11eb-8d9e-11bf52be4c04.png)


### Access Policies

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
My Home Public IP Address
Machines within the network can only be accessed by Jump-Box-Provisioner.
Which machine did you allow to access your ELK VM?
Jump-Box-Provisioner
What was its IP address?
10.0.0.4

A summary of the access policies in place can be found in the table below.


Name	Publicly Accessible	IP Address Allowed
Jump Box	Yes	Home IP Address
Web-1	No	10.0.0.4
Web-2	No	10.0.0.4
Web-3	No	10.0.0.4
Elk-VM	No	10.0.0.4 and Home IP Address![image](https://user-images.githubusercontent.com/85799340/122126822-4baec980-ce00-11eb-9a2f-b5c2123b2db2.png)

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible?
The playbooks can be deployed to any or all VM’s without having to do each 1 by 1.

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
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
- Filebeat and Metrictbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects log files of changes from specified machines and forwards them to Elasticsearch or Logstash for indexing.
Metricbeat collects metrics and statistics from specified machines and forwards them to Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below: 
- Copy the install-elk.yml to /etc/ansible
- Update the hosts file to include
-[elk]
-10.1.0.4 ansible_python_interpreter=/usr/bin/python3

- Run the playbook, and navigate to http://23.99.80.187:5601/app/kibana#/home to check that the installation worked as expected.

_Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Install-elk.yml

-Where do you copy it?_
/etc/ansible/

- _Which file do you update to make Ansible run the playbook on a specific machine? 
-/etc/ansible/hosts

-How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
There is a section in the /etc/ansible/host file where you can put each Virtual Machine with a specific group

-Which URL do you navigate to in order to check that the ELK server is running?
-http://23.99.80.187:5601/app/kibana#/home
