## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below:

![](https://github.com/RandiSpencer/Elk-Stack-Project/blob/main/Network_Diagram_Final.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

 https://github.com/RandiSpencer/Elk-Stack-Project/blob/main/filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting access to the network.

- The aspect of security that load balancers is in the defense of organizations against DDos attacks. It does this by first analyzing the data traffic and then determines where to distribute that traffic accross a number of servers. The purpose is to balance the traffic and shift any malicious traffic the main server.

- The advantage of a jump box is the ability to access and manage devices in a separate security zone.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the configuration and system files.

- Filebeat is a lightweight that monitors log files or specified locations. These logged events are then collected and forwarded to either Elasticsearch or Logstash for indexing. 

- Metricbeat records the metrics and statistics that it collects and ships them to a specified output such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
]']'
| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.9   | Linux            |
| Web-1    | DVWA     | 10.0.0.7   | Linux            |
| Web-2    | DVWA     | 10.0.0.8   | Linux            |                  
| ELK      | ELK      | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP address:

- 20.211.125.67

Machines within the network can only be accessed by the Jump Box Provisioner.

- Using SSH we can access Web-1 (10.0.0.7) and Web-2 (10.0.0.8)  

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible |      Allowed IP Addresses         |
|----------|---------------------|-----------------------------------|
| Jump Box | Yes (SSH Port 22)   | Any                               |
| Web-1    | No (HTTP Port 80)   | 20.211.125.15                     |
| Web-2    | No (HTTP Port 80)   | 20.211.125.15                     |
| ELK      | No (HTTP Port 5601) | 20.211.125.15, 10.0.0.7, 10.0.0.8 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because..

- Ansible can be run from the command line without the use of configuration files for simple tasks to trigger updates across several VM's at once. 

The playbook implements the following tasks:
-Installs Docker.io
-Installs Python3-pip
-Starts Docker on startup

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/103230149/166117280-f6ac08f7-108d-449b-b729-d0f4dc102e11.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
  
- Web-1 10.0.0.7

- Web-2 10.0.0.8


We have installed the following Beats on these machines:

- Filebeats

- Metricbeats

These Beats allow us to collect the following information from each machine:

- Filebeats collects and sends log from Web-1 and Web-2
- Metricbeats collects and records statistics and metrics then sends them to a specified output (eg.Elasticsearch or Logstash)

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to Ansible Container.
- Update the hosts file to include the webservers
- Run the playbook, and navigate to /etc/ansible to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
https://20.211.125.15/app/kibana
