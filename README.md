## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? The load balancer helps to protect the system from DOS attacks.  It also gives the VMS in the pool a forward facing IP that is accessed by the internet.
	This allows for if, say one of the web VMs goes down the load balancer can redirect traffic to the other machines in the pool.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- _TODO: What does Filebeat watch for? Filebeat monitors files for suspicious activity.
- _TODO: What does Metricbeat record? Metricbeat collects machine metrics.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function   | IP address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| Web-1    | Webserver  | 10.0.0.5   | Linux            |
| Web-2    | Webserver  | 10.0.0.6   | Linux            |
| Web-3    | Webserver  | 10.0.0.7   | Linux            |
| Elk      | ELK server | 10.1.0.4   | Linux            | |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 69.121.45.133

Machines within the network can only be accessed by the Jump Box.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? 
   The Jump box - 10.0.0.4


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- Install Docker.io
- Install Python3-pip
- Install Docker module
- Increase Virtual memory
- Download and launch Docker Elk Container
- Enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-10.0.0.5 
-10.0.0.6 
-10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
-Filebeat is a lightweight shipper for forwarding and centralizing log data.  It will send data about the file system such as which files have been changed and when too Logstash and Elasticsearch.
- Metricbeat will collect machine metrics such as uptime and CPU usage.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the .yml files to /etc/ansible 
- Update the hosts file to include :
	[webservers]
	10.0.0.5
        10.0.0.6
        10.0.0.7
    
        [elk]
        10.1.0.4

- Run the playbooks, and navigate to http://[webvmsIPs]/setup.php to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? The .yml files are the playbooks and you copy them to /etc/ansible 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? You edit the hosts file located in /etc/ansible.  You specify the machine to install elk on by adding that machines private ip under the [elk] tab to specify the machines to install filebeat on you simply add those machines private IPs under the [webservers] tag in the /etc/ansible/host file.
- To check if the ELK server is running, navigate to http://[your.Elk-lsVM.IP]:5601/app/kibana



_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._