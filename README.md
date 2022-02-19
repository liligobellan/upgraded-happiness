## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/Network_diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
 Load Balacers defends an organization against distributed denial-of-service (DDoS) attacks.
 A jump box is a secure computer that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- _TODO: What does Filebeat watch for?_ Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- _TODO: What does Metricbeat record?_ Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as Apache.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.2.4 (private-ip) | Linux            |
| Elk-Server| Server  | 10.1.0.5 (private-ip) | linux            |
| Web-1    | Server   | 10.0.0.6 (private-ip) | Linux            |
| Web-2    | Server   | 10.0.0.7 (private-ip) | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the machine Jump-box can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by Jump-Box-Provisioner.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
 Jump-Box is only allowed to access the ElK vm. (10.0.2.4 private ip) 
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump-Box | Yes                 | 10.0.2.4 (private-ip)|
| Elk-Server| No                 | 10.0.2.4             |
| Web-1    | No                  | 10.0.2.4             |
| Web-2    | No                  | 10.0.2.4

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
 Ansible lets you model even highly complex IT workflows, and easy to work with no special skills to get the hang of it. 

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ssh into your Jump-box vm ( ssh username@jumpbox-ip), check for the docker container status (sudo docker ps), start/attach to the container.
- Create a playbook to install docker.
- Then run the playbook in the same directory ( ansible-playbook elk-playbook.yml)
- ssh to your ElK vm to verify that your docker is running. 
 
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
Filbeat and Metricbeat 

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._ 
 Filebeat monitors the log files and collects log events and also forwards them to either to Elasticsearch or Logstash for indexing.
 Metricbeat collect metrics from the operating system and from services running on the server, takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or either Logstash.
Just to have more data of the vm status and the health while running. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ .yml files are playbooks and should be intalled to a docker container directory that you are running. 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ On the hosts file and update that file by adding your webservers and Elk server private ips and ansible_python_interpreter=/usr/bin/python3 beside of it.
- _Which URL do you navigate to in order to check that the ELK server is running? http://elk-ip:5601/app/kibana 

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
 

