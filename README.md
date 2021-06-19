# Project1Week13MM
Project 1 Week 13 Cybersecurity 
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagram](https://github.com/marysiamack/Project1Week13MM/blob/main/Project%201%20Network%20Diagram.png/?raw=true "Diagram")

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml files may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


## Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

### Load balancing ensures that the application will be highly dynamic, in addition to restricting access to the network.
 -What aspect of security do load balancers protect? 
### Load balancers add an additional layver of security. 
 -They protect from emerging threats and the network distribution. They sit amidst the clients devices and backend servers. 
### What is the advantage of a jump box?
 - The advantage of jump box is that it's a secure virtual computer that allows access into servers. It provides security in that it should only work for one machine, or some type of authentication.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the configuration and system files.
### What does Filebeat watch for? 
  -These are open-source lightweight data shippers that are used to send data to Elasticsearch. Filebeat can send data directly to Elasticsearch or through Logstash. Logstash is where ou can even further break down and process through the operational data. Essentially it's a way to centralize the data.
### What does Metricbeat record? 
  -Metricbeat collects metrics from operating systems and services that are on the server. 

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-1    | Webserver| 10.0.0.5   | Linux            |
| Web-2    | Webserver| 10.0.0.6   | Linux            |
| ElkNetVM | Webserver| 10.1.0.4   | Linux            |

## Access Policies

The machines on the internal network are not exposed to the public Internet. 

### Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: My IP address. 
- The only "whitelisted" IP is my own personal IP. 

Machines within the network can only be accessed by The JumpBox Provisioner.
### Which machine did you allow to access your ELK VM? 
    The JumpBox Provisioner was used to gain access within my machine. 
### What was its IP address? 
    Private 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.1             |
| Web-1    | No                  | My IP                |
| Web-2    | No                  | My IP                |
| ElkNetVM | No                  | My IP                |

## Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because now when changes are made they will be made within all the VM's associated within the ansible. 

### What is the main advantage of automating configuration with Ansible? 
The main advantage is that it's efficient for a business in that it's scalable, consistent and reliable.

### The playbook implements the following tasks:
- One task is that it boots on start 
- It installs Docker 
- Playbook downloads and launches 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

## Target Machines & Beats
This ELK server is configured to monitor the following machines:
### - List the IP addresses of the machines you are monitoring
    -ElkNetVM 10.1.0.4
    -JumpBoxProvisioner 10.0.0.4
    -Web-1 10.0.0.5
    -Web-2 10.0.0.6

### We have installed the following Beats on these machines:
    -Filebeat
    -MetricBeat

### These Beats allow us to collect the following information from each machine:
  - Filebeat monitors and logs data from all locations within the server that are specified and then forwards the data to Elasticsearch or Logstash for indexing. 
  - Metricbeat collects metrics from the operating system. For example it would monitor RAM and network usage running on the servers and ship them to Elasticsearch. 

## Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

### SSH into the control node and follow the steps below:
  - Copy the .yml files file to /etc/ansible.
  - Update the /etc/ansible/hosts file to include the webservers.
  - Run the playbook, and navigate to /etc/filebeat/ to check that the installation worked as expected.

### Which file is the playbook? Where do you copy it?
   - /etc/ansible/roles/filebeat-playbook.yml and /etc/ansible/roles/metricbeat-playbook.yml
   - The above playbooks are copied into the ansible container.
### Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? 
   /etc/ansible/hosts file would need to be edited to determine how the playbook will install specific programs. The IP addresses would have to be specified as well. 
### Which URL do you navigate to in order to check that the ELK server is running?
   -http://ELKVMip:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
 To update and communicate with the repository 
 -git add .
 -git push
 -git commit -m "First commit"
