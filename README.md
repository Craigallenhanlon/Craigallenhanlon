## Automated ELK Stack Deployment

![Cloud_Network_Diagram](https://user-images.githubusercontent.com/105895191/170169905-41e083ee-379d-4fa3-abe2-c5ad9c688850.png)

![Azure_ELK_VM](https://user-images.githubusercontent.com/105895191/170377598-99d331de-eae4-4c0a-8673-fa28c62ff749.png)

![ELK png](https://user-images.githubusercontent.com/105895191/170377779-635de1a5-3555-4d09-bfaa-4960e02b366a.png)



The files in this repository were used to configure the network depicted below.
![/c/Users/Cramhole/Craigallenhanlon/Diagrams](Images/diagram_filename.png)
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the __YAML__ file may be used to install only certain pieces of it, such as Filebeat.
  - filebeat-playbook.yml
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
-  What aspect of security do load balancers protect? Load Balancers protect against denial of service attacks (DDoS).  What is the advantage of a jump box? A jumpbox serves as a gatway to gain entry into a remote network. Many times the primary mode of access is ssh and without the key access is forbidden
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Data and system Logs.
-  What does Filebeat watch for? Filebeat is meant primarily to watch for system logs and forward any changes to the Elasticsearch Host.
-  What does Metricbeat record? Metricbeat is used only for gathering metrics and system resources usage for display in Elasticsearch.
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.2.0.4   | Linux            |
| Web1     | Webserver| 10.2.0.5   | Linux                  
| Web2     | Webserver| 10.2.0.6   | Linux            |
| ELK      | Elastic Stack  | 10.0.0.4   | Linux      |
             
### Access Policies
The machines on the internal network are not exposed to the public Internet.
Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 24.2.74.127
Machines within the network can only be accessed by [Jumpbox].
- Which machine did you allow to access your ELK VM? [Jumpbox]. What was its IP address? [10.2.0.4]
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes-SSH-22          | 24.2.74.127          |
| Web1,2   | No                  | 10.2.0.5/10.2.0.6    |
| ELK      | Yes-5601-Kibana     |  *                   |

### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? It allows for full automation of a specific server and reduces configuration errors.
The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker: Installs the core docker code to the remote server.
- Install Python3_pip: Pip is an installation module that allows for additional docker modules to be installed easier.
- Docker Module: Tells the previous PIP module to install the necessary docker component modules.
- Increase Memory/Use More Memory: A common issue with the ELK Docker image is to little memory. This help fix the issue to allow the server to launch.
- Download and Launch ELK Container: This downloads the ELK docker container and initializes it with the specified ports being published.
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker]![Docker png](https://user-images.githubusercontent.com/105895191/170166624-72eec10f-4aa8-411c-8c28-5cc695ab7e7f.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring: Web1/10.2.0.5  Web2/10.2.0.6 ELK/10.0.0.4

We have installed the following Beats on these machines:
- _We have installed Filebeat and Metricbeat on the following Systems: Web1, Web2, ELK_
These Beats allow us to collect the following information from each machine:
- Filebeats collects system type events such as logins to see who is actively logging into the system.
- Metricbeats collects useful information such as cpu usage and memory, this is particularly useful when seeing if there are any aberant programs or behaviors taking system resources.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:
- Copy the elk_install.yml file file to  /etc/ansible/roles/elk_install.yml.
- Update the hosts file to include attribute, such as [elk], then include your destination ip of the ELK server.
- Run the playbook, and navigate to http://[your_elk_server_ip]:5601/app/kibana to check that the installation worked as expected.
_ Answer the following questions to fill in the blanks:_
- _Which file is the playbook? [ansible-playbook]  Where do you copy it? [The ansible contatiner]
- _Which file do you update to make Ansible run the playbook on a specific machine? [ansible.cfg] How do I specify which machine to install the ELK server on versus which to install Filebeat on?_[The IP address]
- _Which URL do you navigate to in order to check that the ELK server is running? 20.213.61.22:5601/app/Kibana#/home
- 
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._[ansible-playbook /etc/ansible/roles/elk_install.yml]

![Kibana](![Kibana2 png](https://user-images.githubusercontent.com/105895191/170375269-714b2d02-79b7-43af-8fcd-91cba843e69f.png)
)

![Kibana1](https://user-images.githubusercontent.com/105895191/170377914-bc12098d-1959-492e-9c9e-fdfdbce3f100.png)

