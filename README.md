## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat. - beat

Ansible
root@c1e0a059c0b0:~# nano my-playbook1.yml

Filebeat :
root@c1e0a059c0b0:/etc/ansible/roles# nano filebeat-playbook.yml

Metricbeat : 
root@c1e0a059c0b0:/etc/ansible/files# nano metricbeat-config.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network. 
Answer : available ,traffic

- What aspect of security do load balancers protect? 
  Answer: Availability, Web Security 

  What is the advantage of a jump box? 
  Answer: Automation, Security, Network Segmentation, 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- What does Filebeat watch for?_ Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

- What does Metricbeat record?_  Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                 | Function     | IP Address               | Operating System |
|----------------------|----------    |--------------------------|------------------|
| Jump-Box-Provisioner | Gateway      | 10.0.0.4 /52.242.18.55   | Linux            |
| Web1                 |Web Server    | 10.0.0.5                 | Linux            |
| Web2                 |Web Server    | 10.0.0.6                 | Linux            |
| ACME-VM1             |ELK Server    | 10.1.0.4 /52.138.103.192 | Linux            |
| Load Balancer        |Load Balancer | Dynamic IP               | Linux            |
| Workstation          |Access Control| 64.231.21.12             | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible  | Allowed IP Addresses              |
|----------|----------------------|-----------------------------------|
| Jump Box |      No              | MyPublicIPAddress                 |
|   Web1   |      Yes             |   Any on Port 80                  |
|   Web2   |      Yes             |   Any on Port 80                  |
| ACME-VM1 |      No              | MyPublicIPAddress using Port 5601 | 

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
Answer : Easy 1 file configuration to be deployed to multiple machines at the same time. 

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
    -  Allow remote user
    -  Install Docker
    -  Install pip3
    -  Start Docker Module
    - 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines: Web1 and Web2
- _TODO: List the IP addresses of the machines you are monitoring_
Web1 : 10.0.0.5
Web2 : 10.0.0.6

We have installed the following Beats on these machines: ELK Server
- _TODO: Specify which Beats you successfully installed_
FileBeat
MetricBeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat -    monitors the log files or locations that you specify, collects log events, and forwards them either to   
              Elasticsearch or Logstash for indexing.
Metricbeat -  takes the metrics and statistics that it collects and ships them to the output that you specify, such as  
              Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the  /etc/ansible/files/filebeat-config.yml file to  /etc/filebeat/filebeat.yml
- Update the _____ file to include... Answer : configuration, hosts, username, password
- Run the playbook, and navigate to ____ to check that the installation worked as expected. localhost or ELK Server

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? yml /etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? config file yml
- _Which URL do you navigate to in order to check that the ELK server is running? http://[your.ELK-VM.External.IP]:5601/app/kibana


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
root#: ansible-playbook playbook.yml
