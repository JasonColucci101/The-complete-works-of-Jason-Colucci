# The-complete-works-of-Jason-Colucci
All of my things in one location 
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. 
They can be used to either recreate the entire deployment pictured above. 
Alternatively, select portions of the yaml file may be used to install only certain pieces of it, such as Filebeat.

  - Ancible.cfg

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
- Load balancers make sure the server stay available by resticting traffic and distributing traffic across mulitple servers if applicable.
- The Jump Box Provisioner is the only server directly connected to the internet to protect the other VMs.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- Filebeat monitor log files or collects log events.
- Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web 1    | VM       | 10.0.0.7   | Linux            |
| Web 2    | VM       | 10.0.0.8   | Linux            |
| Elk      | Elk Ser. | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only then Jump Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Whitelisted IP addresses 20.55.106.151 Jump Box IP.

Machines within the network can only be accessed by the Jump Box Provisioner.
- The only server that can access the ELk Server is the Jump Box Provisioner 20.55.106.151

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | Private work station
| Web 1    |  No                 | Jump Box via SSH     |
| Web 2    |  No                 | Jump Box via SSH     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible lets you quickly deploy multitier apps. No need to write custom code to automate your systems,
you list the tasks required to be done by creating a playbook, and Ansible will figure out how to get your systems to the condition you want them to be in.

The playbook implements the following tasks:
- Implements different group of machines and different remote users.
- Implements and increases system memory.
- It can install services such as 'docker.io', 'python3-pip'
- It can launch containers with published ports.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1: 10.0.0.7
- Web2: 10.0.0.8

We have installed the following Beats on these machines:
- Both filebeats and Metricbeats on Web 1 and Web 2.

These Beats allow us to collect the following information from each machine:
- Filebeat will collect log events to be monitored and reviews later.
- Metricbeat will collect metrict and system statistics to determine trends in the system.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. 
Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible/
- Update the install-elk.yml file to include the correct user name, and range of ports.
- Run the playbook, and navigate to Kibaba to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_
- Which file is the playbook? 
playbook1.yml 

- Where do you copy it?
Copy it to /ect/ansible/host

- Which file do you update to make Ansible run the playbook on a specific machine? 
nano ansible.cfg file and add in the IP of the machine you need.

- How do I specify which machine to install the ELK server on versus which to install Filebeat on? 
When editing the confige file "nano" the IP of the ELK server has to go in the section specific for the ELK server.
All ohter IPs will be separte. When installing Filebeat, during editing only enter in the IPs of Web-1 and Web-2 and not,
the ELK Stack server.

- Which URL do you navigate to in order to check that the ELK server is running?
http://[your.ELK-VM.External.IP]:5601/app/kibana
