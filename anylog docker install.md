# AnyLog Docker Install

## Prerequisites: 
* A Linux/Ubuntu OS (Recommend 18.04LTS or higher)
* Machine with Internet access
* Docker installed

## Deploying AnyLog 

The deployment process sets the environment and installs an AnyLog node (or nodes) with basic configurations. 

### Setup the Environment
* Download the StackScript container from Docker Hub
<pre>
wget http://172.105.178.102/StackScript $HOME
</pre>

* Run the container
<pre>
bash $HOME/StackScript
</pre>

The StackScript container script will do the following:  
* Update env
* Install unzip, ssh, wget and screen
* Install & configure docker
* Download [AnyLog Deployment package](https://www.google.com/url?q=https://anylog-packages.eu-central-1.linodeobjects.com/anylog-deployment.zip&sa=D&source=editors&ust=1612581360946000&usg=AOvVaw1XtS2vQi6M4sv08Z61VgBz)
* Unzip AnyLog Deployment package 

### Install AnyLog

Execute the following command to install AnyLog:
<pre>
bash $HOME/anylog-deployment/deploy_anylog.sh
</pre>

The script interactively requests the user to determine the type of node or nodes to install and some of the main configuration parameters. 
  The selected deployment and configuration decisions are maintained in an INI file such that the deployment decisions can be replicated in new deployments.

#### The deployments options

| Type     | Nodes deploDetails  | Details  |
| ----------- | ------------| ------  |
| node   | A single node. The type of node is determined by the interactive script  |
| config   | Deployment (or redeployment) of a node (or nodes) based on the config file |
| full   | Master, Operator, Publisher, Query | All types of nodes are deployed  | 
| cluster   | Operator, Publisher, Query | Deployment of all nodes without a master node  |
 
#### Installing additional software
 
The deployment includes the option to install and enable Postgres and Grafana as docker images. 

#### The configuration file
A copy of the configuration is stored in 
```anylog-deployment/support/config``` directory and connection details are saved in ```anylog-deployment/support/credentials.txt```.