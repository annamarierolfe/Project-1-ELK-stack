# Project-1-ELK-stack

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Elk-diagram](Images/Elk-diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____***config and yaml*** file may be used to install only certain pieces of it, such as Filebeat.



  -  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Ansible/ansible.cfg.md
  - https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Ansible/filebeat-config.yml
  -  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Ansible/filebeat-playbook.yml
  -  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Ansible/hosts.yml
  -   https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Ansible/install-elk.yml
  -  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Ansible/metricbeat%20playbook.yml
  -  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Ansible/metricbeat-config.yml

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

| Name       | Function     | IP Address              | Operating System |
| ---------- | ------------ | ----------------------- | ---------------- |
| Jump Box   | Gateway      | 10.0.0.4/20.124.252.129 | Linux            |
| Web-1      | UbuntuServer | 10.0.0.5/20.124.101.1   | Linux            |
| Web-2      | UbuntuServer | 10.0.0.6/20.124.101.1   | Linux            |
| DVWA-Web-3 | UbuntuServer | 10.0.0.7/20.124.101.1   | Linux            |
| ELKserver  | UbuntuServer | 10.1.0.4/52.176.103.134 | Linux            |

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

| Name       | Publicly Accessible | Allowed IP Addresses                 |
| ---------- | ------------------- | ------------------------------------ |
| Jump Box   | Yes                 | local machine public IP address      |
| Web-1      | No                  | 10.1.0.4 on SSH 22                   |
| Web-2      | No                  | 10.1.0.4 on SSH 22                   |
| DVWA-Web-3 | No                  | 10.1.0.4 on SSH 22                   |
| ELKserver  | No                  | Workstation Public IP using TCP 5601 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- What is the main advantage of automating configuration with Ansible?

  Advantage of automating with ansible is having consistent configuration management, in other words, you won't have to configure the applications on every machine manually.  makes it reliable and consistent everytime.

The playbook implements the following tasks:

In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

- Specify a different group of machines:

  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Images/elk-%20diff%20group%20machine.PNG

- Install Docker.io

  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Images/install%20docker.io.PNG

- Install Python-pip

  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Images/python3-pip.PNG

- Install Virtual Memory

  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Images/virtual%20memory.PNG

- Dowload and Launch ELK Docker Container

  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Images/d%26l%20elk%20docker%20container.PNG

- Published ports 5044, 561 and 9200 were made available

  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Images/published%20ports.PNG

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

ELKserver:

https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Images/docker%20ps%20elk.PNG

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
- https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Images/filebeat%20syslog%20start%20project%201%20week%2013.PNG
- Metricbeat is used to monitor VM stats, per CPU core stats, per filesystem stats, memory stats and network stats.
- https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Images/project%201%20%3D%20metric%20beat%20snap.PNG

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- Copy the ***yml Playbook*** file to /etc/ansible folder.
- Update the ***config file*** to include remote users and update the ***hosts*** file to IP addresses on servers list.
- Run the playbook, and navigate to newly configured virtual machine to check the installation worked as expected.

_Answer the following questions to fill in the blanks:_

- _Which file is the playbook? _

  For ansible :  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Ansible/ansible_config.yml

  For Filebeat:  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Ansible/filebeat-playbook.yml

  For Metricbeat:  https://github.com/annamarierolfe/Project-1-ELK-stack/blob/main/Ansible/metricbeat%20playbook.yml

- _Where do you copy it?_

  /etc/ansible

- _Which file do you update to make Ansible run the playbook on a specific machine? 

  Hosts file is the one that specifies the name o the machine to update.

- _How do I specify which machine to install the ELK server on versus which to install Filebeat on?_

  Have to specify it inside the hosts file. One group are the webserver which hae the IPs of the 3 VMs that will install Filebeat to. The other group is name ELK with the IP of the VM installed in ELK.

- _Which URL do you navigate to in order to check that the ELK server is running?

  http://[your.ELK-VM.External.IP]5601/app/kibana



### Sites Used for References and Knowledge for the Project

- [Elastic: The Elastic Stack.](https://www.elastic.co/elastic-stack)
- [Elastic: Filebeat.](https://www.elastic.co/beats/filebeat)
- [ELK Docker Documentation.](https://elk-docker.readthedocs.io/)
- [Microsoft Azure: Global vNet Peering](https://azure.microsoft.com/en-ca/blog/global-vnet-peering-now-generally-available/)
- [Microsoft Docs: How to open a support ticket](https://docs.microsoft.com/en-us/azure/azure-portal/supportability/how-to-create-azure-support-request)
- [Peachpit.com: Split-Half Search](https://www.peachpit.com/articles/article.aspx?p=420908&seqNum=3)
- [Elastic: Filebeat Container Documentation](https://www.elastic.co/beats/filebeat)
- [Phoenixnap.com: Docker Commands Cheat Sheet](https://phoenixnap.com/kb/list-of-docker-commands-cheat-sheet)
- [Docker and Ansible Cloud Week Cheat Sheet](https://www.bogotobogo.com/DevOps/Docker/Docker-Cheat-Sheet.php)
- [Ansible: Roles Playbook Reuse Roles](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html)
- [Elastic: Getting Started with the Elastic Stack](https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-elastic-stack.html)

