## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


https://github.com/damccollum/CyberSecurity-Project-1/blob/main/Diagrams/RedNet%20Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - install-elk.yml, install-filebeat.yml, install-metricbeat.yml

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
- Load balancers attempt to protect a network availability by dispersing network traffic over the available web servers. Load balancing can help mitigate outages caused by denial of service type attacks.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.
- Filebeat monitors for changes made to files and sends logs of the changes to the ELK server.
- Metricbeat collects metrics from services and the operating system on the network and sends logs to the ELK server

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| WEB-1    | Server   | 10.0.0.5   | Linux            |
| WEB-2    | Server   | 10.0.0.6   | Linux            |
| ELK      | Server   | 10.2.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Public IP

Machines within the network can only be accessed by the Jumpbox.
- The Jumpbox (10.0.0.4)

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Public IP via SSH    |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| ELK      | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the network can be deployed quickly and can be rebuilt/redeployed quickly and easily, if ever needed. 

The playbook implements the following tasks:
- Install docker.io
- Install python3-pip
- Install docker module
- Increase Virtual Memory
- Download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (10.0.0.5)
- Web-2 (10.0.0.6)

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors for changes made to files and sends logs of the changes to the ELK server.
- Metricbeat collects metrics from services and the operating system on the network and sends logs to the ELK server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-filebeat.yml and install-metricbeat.yml to /etc/ansible/roles.
- Update the /etc/ansible/hosts file to include the IP addresses of the webserver VMs.
- Run the playbook, and navigate to http://20.110.57.34:5601/app/kibana to check that the installation worked as expected.
