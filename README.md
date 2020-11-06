# cybersecurity_Project
---

ELK

 Project1 Week 13 Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.
 (./Diagrams/HWK12.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbook.yml file may be used to install only certain pieces of it, such as Filebeat.
  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology 
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
Load balancers protect the servers from becoming overloaded with traffic. 
Just like it sounds it balances traffic between servers. Tha avantage of having a Jumpbox having one spot for administrative access so that the servers aren’t accessed from the internet by just anyone.
_
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

 Filebeat watches for log files and collects events.
 Metricbeat records statistical data from the OS and services running on the servers.

The configuration details of each machine may be found below.

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| Web-1    | DVWA Server| 10.0.0.8   | Linux            |
| Web-2    | DVWA Server| 10.0.0.9   | Linux            |
| Web-3    | DVWA Server| 10.0.0.10  | Linux            |
| ELK Serv | ELK Stack  | 10.1.0.4   | Linux            |



 Access Policies
The machines on the internal network are not exposed to the public Internet. 
Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
My personal IP address
Machines within the network can only be accessed by SSH.
The ELK Server is accessed through SSH form the Jump Box from my personal IP address._
A summary of the access policies in place can be found in the table below.
| Name      | Publicly Accessible | Allowed IP Addresses |
|-----------|---------------------|----------------------|
| Jump Box  |     No              | SSH MY IP            |
| Web-1     |    Yes              |13.68.170.91, 10.0.0.4|
| Web-2     |    Yes              |13.68.170.91, 10.0.0.4|
| Web-3     |    Yes              |13.68.170.91, 10.0.0.4|
| ELK Server|    No               |SSH 10.1.0.4:5601     |

### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
 Automating the deployment we can sent it to many machines at one time.
Not needing to write scripts on each machine with the chance of errors.

The playbook implements the following tasks:
* Install Docker.io and pip3
* Change VM Memory size
* Download and Configure ELK docker container
* Set Ports


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
**Note**: The following image link needs to be updated. Replace `docker_ps_output.png` with the name of your screenshot image file.  
![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 10.0.0.8 Web-2 10.0.0.9 Web-3 10.0.0.10
I have installed the following Beats on these machines:
* Filebeat

These Beats allow us to collect the following information from each machine:

Filebeats collects log files on its host. Then transfers the logs to the ELK-server then you can open and inspect them with Kibana.

Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- Copy the filebeat-config.yml file to /etc/ansible/files.
- Update the config file to include the Priviate IP of the ELK server
  To the Elasticsearch and Kibana sections of the config file.

- Run the playbook, and navigate to ELK serves IP:5601/app/kibana to check that the installation worked as expected.

Which file is the playbook? Where do you copy it?_
Elk-playbook.yml, goes to /etc/ansible

Which file do you update to make Ansible run the playbook on a specific machine?  The /etc/ansible/hosts.cfg this is were you add the IP address of the machines you want it installed on.
 
How do I specify which machine to install the ELK server on versus which to install Filebeat on? In the etc/ansible/hosts you can specify what servers to install it on.
Example webserves elkserver.

- _Which URL do you navigate to in order to check that the ELK server is running? 
Navigate to http://publicIP(elkserver):5601




