# UCIELKSTACKPROJECT
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Image of Network](https://github.com/foo2rama/UCIELKSTACKPROJECT/blob/master/NetworkMap.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the configuration file may be used to install only certain pieces of it, such as Filebeat.

  filebeat-config.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose load-balanced and monitored instances of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable, in addition to restricting access to the network.
The configuration of the Web Servers protects the rest of the network from intrusion, as Dockers protect the host machine.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name         | Function       | IP Address |
|--------------|----------------|------------|
| Jump Box     | Network access | 10.10.0.9  |
| Web Server 1 | Webserver      | 10.10.0.10 |
| Web Server 2 | Webserver      | 10.10.0.11 |
| Web Server 3 | Webserver      | 10.10.0.12 |
| ELK Server   | Elk Stack      | 10.1.0.4   |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from computers that have the pgp Key used to create the server.

Machines within the network can only be accessed by SSH with PGPkey access using a key created on the JumpBox.

The one exception is the ELK Stack server which can be accessed via HTTP on port:5601.  

**NOTE** It is recommened that you place an access rule on this machine so that only allowed IP addresses are allowed to connect.


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
Ansible allows us to automate and quickly redeploy all dockers in the network.

The ELK playbook implements the following tasks:
- Installs needed files
- Configures the Server and programs
- Launches the docker containing the configured ELK Stack.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

**Note**: Make sure to run the command "sudo docker ps" on the host server to make sure that the server launched.  If it is unstable and shuts down within the first 2 minutes, you must increase the memory allocated to the cloud server hosting the Docker.

Once launched you can verify the status of the ELK Stack by accessing it a web broswer pointed at its public IP on port 5601.  http://X.X.X.X:5601



We have installed the following Beats on these machines:
Metric Beat and File Beat

These Beats allow us to collect the following information from each machine:
- These Beats will monitor the files on the machine for intrusion, as well as if the server has restarted or has unusal patterns in its cpu, storage, and memory use.


### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to ansible container.
- Update the hosts file to include the correct address for the ELK server and webservers
- Run the playbook, and navigate to Docker hosts to check that the installation worked as expected.  You can run the sudo docker ps command


### TIPS

- I have found keepings the playbooks at the home location on the servers makes life easier
- Te Hosts file is where you specifiy the internal network IP and which groups servers belong.
- The ELK Stack can be accessed by aweb broswer pointed at its public IP on port 5601.  http://X.X.X.X:5601
- if you are attached via a terminal to a docker be carefull using the exit command as it might shut down the docker you are in.  
- if you are in a docker you do not need to type sudo as you are already root.


### Usefull Commands
sudo docker ps (shows active dockers on a machine)
sudo docker container list -a (shows all dockers on the server)
sudo docker start <containername> (starts docker)
sudo docker attach <containername> opens connection to docker)
sudo systemctl restart docker (stop restart the docker daemon)
