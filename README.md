## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Images/diagram_azur.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

- _TODO: Enter the playbook file._
- Elk Playbook.yml
- Metricbeat.yml  
- Filebeatplaybook.yml
- Myplaybook.yml


This document contains the following details:
- Description of the Topologu : topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _available_, in addition to restricting _access_ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
      Access is controlled toa vulnerable host via the jumpbox. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _event logs_ and system _metrics_.
- _TODO: What does Filebeat watch for?
      - Filbeats watch for log directories or specific log files
- _TODO: What does Metricbeat record?
      - Metricbeats records or collect metrics from the operating system and from services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   |  Linux           |
| web 1    |  host    | 10.1.0.5   |  Linux           |
| web 2    |  host    | 10.1.0.7   |  Linux           |
| ELK-vm   |  logs    | 10.3.0.5   |  Linux           |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _jumpbox_ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_
      The Elk Machine can have access from personal IP address () through port 5601.

Machines within the network can only be accessed by _jumpbox_.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
        The Elk Machine can have access from personal IP address (47.221.11.253 ) through port 5601.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              |  47.221.11.253       |
|   web 1  |    NO               |     10.1.0.5         |
|   web 2  |    NO               |     10.1.0.7         |
|   ELK    |    YES              |     10.1.0.4
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
     You can run a playbook that wil configure multipole machine at the same time with the exact configuration. Simple to configure, human readable and commands are ran in the order they're written.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...
  - Installed Docker.io into system
  - Installed Python3Pip package manager
  - Installed Python package docker
  - Download Elk image and open the ports for kibana usage


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
 - Web -1 : 10.0.0.5
 - Web -2 : 10.0.0.7

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
 - Filebeat
 - Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

Filebeat is a log data shipper for local files. Installed as an agent on your servers, Filebeat monitors the log directories or specific log files, tails the files, and forwards them either to Elasticsearch or Logstash for indexing. An examle of such are the logs produced from the MySQL database supporting our application.
Metricbeat collects metrics and statistics on the system. An example of such is cpu usage, which can be used to monitor the system health



### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _Ansible/Elk playbook.yml_ file to _/etc/files_.
- Update the _/etc/ansible/hosts_ file to include...group of machines you're trying to run the playbook
- Run the playbook, and navigate to _http://20.114.141.161:5601/app/kibana_ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?
   _ The Filebeat-configuration
   _copy /etc/ansible/files/filebeat-config.yml to /etc/filebeat/filebeat.yml

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
     _update filebeat-config. yml -- specify which machine to install by updating the host files 
     with ip addresses of web/elk servers and selecting which group to run on in ansible

- _Which URL do you navigate to in order to check that the ELK server is running?
 http://20.114.141.161:5601/app/kibana


_As a **Bonus**, provide the specific 
commands the user will need to run to download the playbook, update the files, etc._