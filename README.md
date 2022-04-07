## Automated ELK Stack Deployment 
 
The files in this repository were used to configure the network depicted below. 
 
https://drive.google.com/file/d/1NPNcE79ZFbdYPUkEbH20S5cUv3Q6xe3O/view?usp=sharing

 
 
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat. 
 
  ~/etc/ansible/elkconfig.yml 
 
This document contains the following details: 
- Description of the Topologu 
- Access Policies 
- ELK Configuration 
  - Beats in Use 
  - Machines Being Monitored 
- How to Use the Ansible Build 
 
 
### Description of the Topology 
 
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application. 
 
Load balancing ensures that the application will be highly Available, in addition to restricting attacks to the network. 
Load balancing is a way an application can become highly availlable for its consumers, while also adding an extra layer of defense. And having the jumpbox being the access into the virtual network is a huge security bonus. 
 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic. 
Filebeat is a service which monitors specific log files or locations, collecting any event logs, and packages to be easily accessed by Elasticsearch or logstash for indexing. 
Being an extremely efficent, easy to use, and reliable meteric shipper that moniotors your system and processed running. Here are the configuration details of each machine. 
 
The configuration details of each machine may be found below. 
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_. 
 
| Name     | Function | IP Address | Operating System | 
|----------|----------|------------|------------------| 
|Jump-Box-Provisioner|Gateway|Public:40.78.122.215 Private:10.0.0.4|Linux| 
|Web-1|Server|10.0.0.5|Linux| 
|Web-3|Server|10.0.0.7|Linux| 
|ELK-SERVER|Monitoring|Public:20.25.65.80 Private:10.1.0.4|Linux| 
 
### Access Policies 
 
The machines on the internal network are not exposed to the public Internet.  
 
Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
104.176.34.132 
Machines within the network can only be accessed by Jump-Box-Provisioner. 
20.25.65.80:5601 
137.117.22.25 
 
A summary of the access policies in place can be found in the table below. 
 
| Name     | Publicly Accessible | Allowed IP Addresses | 
|----------|---------------------|------------------------| 
| Jump Box       |Yes                  |104.176.34.132| 
| Web-1             |No                   |10.0.0.4            | 
| Web-3             |No                   |10.0.0.4            | 
| ELS-SERVER|No                   |10.0.0.4            | 
 

 
### Elk Configuration 
 
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because... 
Automating tasks makes them run quicker, and simpler while also preventing easily overlooked vulnerably.  
 
The playbook implements the following tasks: 
 

    Install docker.io 

    Install python3-pip 

    Install docker via pip 

    Increase vitual memory 

    Use more memory 

    Download and launch a docker elk container - starts docker and establishes the ports being used. 

 
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance. 
 
https://drive.google.com/file/d/1OeVLkU8NHgCpRyY0Wsb1LKb1X4t2upaT/view?usp=sharing
 
### Target Machines & Beats 
This ELK server is configured to monitor the following machines: 
Web-1 10.0.0.5 

Web-3 10.0.0.7 
 
We have installed the following Beats on these machines: 

Filebeat and Metric beat onto: 

Web-1 10.0.0.5 

Web-3 10.0.0.7 

ELK-SERVER 20.25.65.80 
 
These Beats allow us to collect the following information from each machine: 
Filebeat allows collection of log data and displays them in a monitored cluster. While metricbeat is the collection of metrics and statistics and displays them in a specified output for Elasticsearch or Logstah 
 
### Using the Playbook 
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:  
 
SSH into the control node and follow the steps below: 
- Copy the elkconfig.yml file to Ansible directory. 
- Update the host file to include the webserver hosts and ELK-SERVER. 
- Run the playbook, and navigate to Kibana to check that the installation worked as expected. (104.176.34.132:5601/app/kibana) 

- _Which file is the playbook? Elkconfig.yml Where do you copy it? To /etc/ansible/_ 
- _Which file do you update to make Ansible run the playbook on a specific machine? /etc/ansible/hosts How do I specify which machine to install the ELK server on versus which to install Filebeat on? In the hosts file there is a place to specify_ 
- _Which URL do you navigate to in order to check that the ELK server is running?  
104.176.34.132:5601/app/kibana 