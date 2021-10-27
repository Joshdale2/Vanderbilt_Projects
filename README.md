# Vanderbilt_Projects
Projects and assignments completed throughout the Cybersecurity Bootcamp

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Vandy-BC/Diagrams/Azure Cloud Diagram.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  - Vandy-BC/Ansible/Filebeat Playbook.txt

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting burden to the network.
- Load balancers help the availability of an application. A jump box is a secure host that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system Logs.
- Filebeat watches for log files and events.
- Metricbeat collects metrics from the system and services running on the server.

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway | 10.0.0.6 | Linux          |
| Web-1      | VM        | 10.0.0.7   | Linux        |
| Web-2      | VM        | 10.0.0.8   | Linux        |
| Web-3      | VM        | 10.0.0.9   | Linux        |
| Elk           | Elk Stack| 10.1.0.4  | Linux         |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the gateway machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 75.46.245.151

Machines within the network can only be accessed by Jump Box.
- The jump box machine using the ansible container within has access to the elk vm. IP address 10.0.0.6

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes               | 75.46.245.151     |
| Web-1    | No                  | 10.0.0.6             |
| Web-2    | No                  | 10.0.0.6             |
| Web-3    | No                  | 10.0.0.6             |
| Web-4    | No                  | 10.0.0.6             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible automation helps considerably with daily tasks and simple network management.

The playbook implements the following tasks:
- Install docker.io
- Install python3-pip
- Install docker module
- Increase Virtual memory
- Use more memory on restart
- Download and launch a docker elk container
- Enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Vanderbilt_Projects/Images/Elk_Docker_Example.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.6
- 10.0.0.7
- 10.0.0.8
- 10.0.0.9

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat_Playbook.yml to /etc/ansible.
- Update the /etc/ansible/hosts file to include...
- 
-[webservers]
-0.0.0.0 ansible_python_interpreter=/usr/bin/python3
-[elk]
-0.0.0.0 ansible_python_interpreter=/usr/bin/python3

- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.
