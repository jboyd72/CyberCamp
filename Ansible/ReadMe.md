## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagram](https://github.com/jboyd72/ELK-Stack-Deployment/blob/main/Ansible/ELK_Stack_Cloud_Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

- ![Filebeat Playbook](https://github.com/jboyd72/ELK-Stack-Deployment/blob/main/Ansible/filebeat_playbook.yml)
- ![Metricbeat Playbook](https://github.com/jboyd72/ELK-Stack-Deployment/blob/main/Ansible/metricbeat_playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable and available, in addition to restricting access to the network. Load balancers also protect against a DdoS attack by distributing traffic accross mutiple servers. The Jump box allows for easy configuration for all servers from one central server.

Integrating an ELK server allows users to easily monitor the vulnerable Vms for changes to the log files and system metrics.
- filebeat collects log data from the system.
- metricbeat collects machine metrics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux
| Web 1    |  Server  | 10.0.0.7   | Linux
| Web 2    |  Server  | 10.0.0.8   | Linux
| Web 3    |  Server  | 10.0.0.10  | Linux
### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Load Balancer can accept connections from the Internet. Access to the Load Balancer is only allowed from the Host machine.

Machines within the network can only be accessed by the JUMP BOX
- The public IP of the Jump Box.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 10.0.0.7 , 10.0.0.8 , 10.0.0.10  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it will ensure the scripts run identically everywhere, every time, which further reduces unneccecssary vulneralbilities.

The playbook implements the following tasks:
-	Installs docker.io
- Installs python3
- Installs docker ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Screenshot](https://github.com/jboyd72/ELK-Stack-Deployment/blob/main/Ansible/ELK_docker_ps_screenshot.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1 10.0.0.7
- Web2 10.0.0.8
- Web3 10.0.0.10

We have installed the following Beats on these machines:
- filebeat
- metricbeat

These Beats allow us to collect the following information from each machine:
- filebeat collects log data from the system.
- metricbeat collects machine metrics.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- copy filebeat-playbook.yml into /etc/ansible.
- update the conigureation file to include the IP address of the ELK machine.
- Run the playbook and navigate to http://(ELK VM IP):5601/app/kibana to see if the installation worked as expected.
