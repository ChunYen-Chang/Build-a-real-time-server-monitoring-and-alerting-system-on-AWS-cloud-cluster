<p align="center">
  <img width="750" height="280" src="https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/project_logo.jpg">
</p>
  
  
# Build a Real-Time Server Monitoring and Alerting System on AWS Cloud Cluster
-----
### *Real-time server monitor system dashboard*
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/037.png)
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/038.png)

### *Immediately Notify system errors through E-mail*
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/057.png)

-----
### *SYSTEM ARCHITECTURE*
-----

### *STEP BY STEP LAUNCHING INSTRUCTION*

**FIRST PART: PREPARATIONs**
- Step 1: Launch three AWS EC2 instances (One Prometheous master node, two monitored nodes)
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/001.png)

- Step 2: Define the security group (virtual firewall) for Prometheous master node
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/002.png)
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/003.png)

- Step 3: Define the security group (virtual firewall) for monitored nodes
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/004.png)
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/005.png)

**SECOND PART: INSTALL PROMETHEOUS MASTER**
- Step 1: SSH to thr Prometheous master node
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/006.png)

- Step 2: type `wget https://github.com/prometheus/prometheus/releases/download/v2.17.1/prometheus-2.17.1.linux-amd64.tar.gz` for downloading Prometheous master node program
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/007.png)

- Step 3: type `tar -xzf prometheus-2.17.1.linux-amd64.tar.gz` for unzipping the file
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/008.png)

- Step 4: Remove **prometheus-2.17.1.linux-amd64.tar.gz**
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/009.png)

- Step 5: Change directory to **prometheus-2.17.1.linux-amd64**
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/010.png)

- Step 6: Modify the prometheous config file - **prometheus.yml**
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/011.png)
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/012.png)

- Step 7: Launch Prometheous master server by typing `./prometheous`
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/013.png)

- Step 8: Access to the server to check whether it is success or not
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/014.png)
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/015.png)


**THIRD PART: INSTALL NODE_EXPORTER**
- Step 1: SSH to nodes you want to monitor, in this project, we want to monitor prometheous master node and other two nodes
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/006.png)

- Step 2: type `wget https://github.com/prometheus/node_exporter/releases/download/v0.18.1/node_exporter-0.18.1.linux-amd64.tar.gz` for downloading node_exporter
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/016.png)

- Step 3: type `tar -xzf node_exporter-0.18.1.linux-amd64.tar.gz` for unzipping the file
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/017.png)

- Step 4: Remove **node_exporter-0.18.1.linux-amd64.tar.gz**
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/018.png)

- Step 5: Change directory to **node_exporter-0.18.1.linux-amd64**
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/019.png)

- Step 6: Launch Prometheous master server by typing `./node_exporter`
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/020.png)
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/021.png)

- Step 7: Access to these nodes to check whether node_exporter work properly or not
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/022.png)

- Step 8: Access to the Prometheous master server to check whether Master catches all nodes information or not
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/023.png)
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/024.png)

**FOURTH PART: INSTALL GRAFANA**
- Step 1: SSH to Prometheus master server
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/006.png)

- Step 2: Download Grafana by typing `wget https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana-3.1.1-1470047149.linux-x64.tar.gz`
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/025.png)

- Step 3: unzip the file by typing `tar -zxvf grafana-3.1.1-1470047149.linux-x64.tar.gz`
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/026.png)

- Step 4: Remove **grafana-3.1.1-1470047149.linux-x64.tar.gz**
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/027.png)

- Step 5: Change directory to **grafana-3.1.1-1470047149.linux-x64**
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/028.png)

- Step 6: Launch the Grafana server by typing `./bin/grafana-server`
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/029.png)

- Step 7: Access to Grafana server
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/030.png)

- Step 8: Type the default username and password, **admin**, to log in.
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/031.png)

- Step 9: Click configuration icon on the left panel to tell Grafana to get the data from Prometheus
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/032.png)

- Step 10: Relelating settings in Step 9
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/033.png)
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/034.png)

- Step 11: Clicl import icon on the left panel to import Grafana dashboard which already created by others to presnet your data
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/035.png)

- Step 12: Relelating settings in Step 11
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/036.png)

- Step 13: Use the dashboard to present the system data from each monitored nodes
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/037.png)
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/038.png)

- Step Bonus: You can choose the dashboard layout you like ! For example.... 
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/039.png)
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/040.png)

**FINAL PART: INSTALL PROMETHEOUS ALERTMANAGER**
- Step 1: SSH to Prometheus master server
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/006.png)

- Step 2: Change directory to **prometheus-2.17.1.linux-amd64**
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/042.png)

- Step 3: Create a alerting rule config file called **rules.yml**
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/041.png)

- Step 4: Define alerting rules in this config file
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/044.png)

- Step 5: Open **prometheus.yml** to check this file already has relating setting for alerting rules and for alerting managers
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/045.png)

- Step 6: Change directory to root directory

- Steo 7: Download Alertmanager by typing `wget https://github.com/prometheus/alertmanager/releases/download/v0.20.0/alertmanager-0.20.0.linux-amd64.tar.gz`
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/046.png)

- Step 8: Unzip **alertmanager-0.20.0.linux-amd64.tar.gz**
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/047.png)

- Step 9: Remove **alertmanager-0.20.0.linux-amd64.tar.gz**
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/048.png)

- Step 10: Change directory to **alertmanager-0.20.0.linux-amd64**
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/050.png)

- Step 11: Modify **alertmanager.yml** to allow Alertmanager send an email to us when instance errors occur
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/051.png)

- Step 12: Relelating settings in Step 10
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/052.png)

- Step 13: Launch Alertmanager by typing `./alertmanager --config.file=alertmanager.yml`
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/053.png)

- Step 14: Shutting down one node_exporter to see whether we can get the email notification or not
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/054.png)
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/055.png)

- Step 15: Make sure alert manager receives the error message
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/056.png)

- Step 14: We receive the notification email!
![](https://github.com/ChunYen-Chang/Build-a-real-time-server-monitoring-and-alerting-system-on-AWS-cloud-cluster/blob/master/image/057.png)
