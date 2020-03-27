<p align="center">
  <img width="750" height="280" src="https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/project_logo.jpg">
</p>
  
  
# Build a Real-Time Server Monitoring and Alerting System on AWS Cloud Cluster


### *SYSTEM ARCHITECTURE*


### *STEP BY STEP LAUNCHING INSTRUCTION*

**FIRST PART: PREPARATIONs**
- Step 1: Launch three AWS EC2 instances (One Prometheous master node, two monitored nodes)
- Step 2: Define the security group (virtual firewall) for Prometheous master node
- Step 3: Define the security group (virtual firewall) for monitored nodes

**SECOND PART: INSTALL PROMETHEOUS MASTER**
- Step 1: SSH to thr Prometheous master node
- Step 2: type `wget https://github.com/prometheus/prometheus/releases/download/v2.17.1/prometheus-2.17.1.linux-amd64.tar.gz` for downloading Prometheous master node program
- Step 3: type `tar -xzf prometheus-2.17.1.linux-amd64.tar.gz` for unzipping the file
- Step 4: Remove **prometheus-2.17.1.linux-amd64.tar.gz**
- Step 5: Change directory to **prometheus-2.17.1.linux-amd64**
- Step 6: Modify the prometheous config file - **prometheus.yml**
- Step 7: Launch Prometheous master server by typing `./prometheous`
- Step 8: Access to the server to check whether it is success or not


**THIRD PART: INSTALL NODE_EXPORTER**
- Step 1: SSH to nodes you want to monitor, in this project, we want to monitor prometheous master node and other two nodes
- Step 2: type `wget https://github.com/prometheus/node_exporter/releases/download/v0.18.1/node_exporter-0.18.1.linux-amd64.tar.gz` for downloading node_exporter
- Step 3: type `tar -xzf node_exporter-0.18.1.linux-amd64.tar.gz` for unzipping the file
- Step 4: Remove **node_exporter-0.18.1.linux-amd64.tar.gz**
- Step 5: Change directory to **node_exporter-0.18.1.linux-amd64**
- Step 6: Launch Prometheous master server by typing `./node_exporter`
- Step 7: Access to these nodes to check whether node_exporter work properly or not
- Step 8: Access to the Prometheous master server to check whether Master catches all nodes information or not

**FOURTH PART: INSTALL GRAFANA**
- Step 1: SSH to Prometheous master server
- Step 2: Download Grafana by typing `wget https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana-3.1.1-1470047149.linux-x64.tar.gz`
- Step 3: unzip the file by typing `tar -zxvf grafana-3.1.1-1470047149.linux-x64.tar.gz`
- Step 4: Remove **grafana-3.1.1-1470047149.linux-x64.tar.gz**
- Step 5: Change directory to **grafana-3.1.1-1470047149.linux-x64**
- Step 6: Launch the Grafana server by typing `./bin/grafana-server`
- Step 7: Access to Grafana server
- Step 8: Type the default username and password, **admin**, to log in
- Step 9: Set up a new password
- Step 10: Click configuration icon on the left panel to tell Grafana to get the data from Prometheous
- Step 11: Rerelating settings in Step 10
- Step 12: Clicl import icon on the left panel to import Grafana dashboard which already created by others to presnet your data
- Step 13: Rerelating settings in Step 12
- Step 14: Use the dashboard to present the system data from each monitored nodes

**FINAL PART: INSTALL PROMETHEOUS ALERTMANAGER**
- Step 1: SSH to Prometheous master server
- Step 2: Create a alerting rule config file called **instance_alert_rules.yml**
- Step 3: Define alerting rules in this config file
- Step 4: Open **prometheous.yml** to check this file already has relating setting for alerting rules and for alerting managers
- Step 5: Change directory to root directory
- Steo 6: Download Alertmanager by typing `wget https://github.com/prometheus/alertmanager/releases/download/v0.20.0/alertmanager-0.20.0.linux-amd64.tar.gz`
- Step 7: Unzip **alertmanager-0.20.0.linux-amd64.tar.gz**
- Step 8: Modify **alertmanager.yml** to allow Alertmanager send an email to us when instance errors occur
- Step 9: Launch Alertmanager by typing `./alertmanager --config.file=alertmanager.yml`
- Step 10: Shutting down one node_exporter to see whether we can get the email notification or not
- Step 11: We receive it!
