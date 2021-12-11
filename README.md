# Project-1-ELK-stack

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Elk-diagram](Images/Elk-diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.



  -  [ansible_config.yml](..\..\..\..\..\Project-1-ELK-stack\Ansible\ansible_config.yml) 
  -  [filebeat-config.yml](..\..\..\..\..\Project-1-ELK-stack\Ansible\filebeat-config.yml) 
  -  [filebeat-playbook.yml](..\..\..\..\..\Project-1-ELK-stack\Ansible\filebeat-playbook.yml) 
  -  [hosts.yml](..\..\..\..\..\Project-1-ELK-stack\Ansible\hosts.yml) 
  -  [install-elk.yml](..\..\..\..\..\Project-1-ELK-stack\Ansible\install-elk.yml) 
  -  [metricbeat playbook.yml](..\..\..\..\..\Project-1-ELK-stack\Ansible\metricbeat playbook.yml) 
  -  [metricbeat-config.yml](..\..\..\..\..\Project-1-ELK-stack\Ansible\metricbeat-config.yml) 

This document contains the following details:

- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly ***functional and available***, in addition to restricting ***traffic*** to the network.

- What aspect of security do load balancers protect? 

  A load balancer can add additional layer of security to a website without any changes to you application, it evenly distribute network traffic to prevent failure caused by overloading a particular resource.

- What is the advantage of a jump box?

  Jump box is advantageous in a way where it acts as an audit for traffic and a single point where we can manage user accounts.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the ***network*** and system ***logs***.

- **What does Filebeat watch for?**

  Filebeat monitors the log files or locations that is specified, collects log events and forwards them either to Elasticsearch or Logstash for indexing.

- **What does Metricbeat record?**

  Metricbeat takes the metrics and statics that it collects and ship them to the output that is specified, such as Elasticsearch or Logstash. Its helps you monitor your servers by collecting metrics from the system and services running on the server, such as: Apache.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function     | IP Address              | Operating System |
| --------- | ------------ | ----------------------- | ---------------- |
| Jump Box  | Gateway      | 10.0.0.4/20.124.252.129 | Linux            |
| Web-1     | UbuntuServer | 10.0.0.5/20.124.101.1   | Linux            |
| Web-2     | UbuntuServer | 10.0.0.6/20.124.101.1   | Linux            |
| Web-3     | UbuntuServer | 10.0.0.7/20.124.101.1   | Linux            |
| ELKserver | UbuntuServer | 10.1.0.4/52.176.103.134 | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ***Jump-Box-Provisioner*** machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- Workstation public IP through TCP 5601

Machines within the network can only be accessed by ***Elk VM and Jump-Box-Provisioner through SSH Jump-Box***.

- Which machine did you allow to access your ELK VM? 

  Jump-Box-Provisioner IP: 10.0.0.4 via SSH port 22

- _What was its IP address?_

  ELK VM public IP through TCP 5601

  

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses                 |
| --------- | ------------------- | ------------------------------------ |
| Jump Box  | Yes                 | (Workstation IP on SSH 22)           |
| Web-1     | No                  | 10.1.0.4 on SSH 22                   |
| Web-2     | No                  | 10.1.0.4 on SSH 22                   |
| Web-3     | No                  | 10.1.0.4 on SSH 22                   |
| ELKserver | No                  | Workstation Public IP using TCP 5601 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- What is the main advantage of automating configuration with Ansible?

  Advantage of automating with ansible is having consistent configuration management, in other words, you won't have to configure the applications on every machine manually. 

The playbook implements the following tasks:

In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

- Specify a different group of machines:

  ![elk- diff group machine](C:\Users\annam\OneDrive\Documents\README\README\Images\elk- diff group machine.PNG)

- Install Docker.io

  ![install docker.io](C:\Users\annam\OneDrive\Documents\README\README\Images\install docker.io.PNG)

- Install Python-pip

  ![python3-pip](C:\Users\annam\OneDrive\Documents\README\README\Images\python3-pip.PNG)

- Install Virtual Memory

  ![virtual memory](C:\Users\annam\OneDrive\Documents\README\README\Images\virtual memory.PNG)

- Dowload and Launch ELK Docker Container

  ![d&l elk docker container](C:\Users\annam\OneDrive\Documents\README\README\Images\d&l elk docker container.PNG)

- Published ports 5044, 561 and 9200 were made available

  ![published ports](C:\Users\annam\OneDrive\Documents\README\README\Images\published ports.PNG)

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

ELKserver:

![docker ps elk](C:\Users\annam\OneDrive\Documents\README\README\Images\docker ps elk.PNG)

### Target Machines & Beats

This ELK server is configured to monitor the following machines:

- Web-1: 10.0.0.5
- Web-2: 10.0.0.6
- Web-3: 10.0.0.7

We have installed the following Beats on these machines:

- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:

- Filebeat is used to collect log files from specific files such as Microsoft Azure, Apache and webservers, MySQL databases.
- Metricbeat is used to monitor VM stats, per CPU core stats, per filesystem stats, memory stats and network stats.

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- Copy the Playbook file to /etc/ansible folder.
- Update the ___hosts__ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_

- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
