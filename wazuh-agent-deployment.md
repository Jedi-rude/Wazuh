# Wazuh Agent Deployment
Wazuh is a free and open source platform used for threat prevention, detection, and response. It is capable of protecting workloads across on-premises, virtualized, containerized, and cloud-based environments.

## Deploy Windows agent
The Wazuh agent is multi-platform and runs on the endpoints that the user wants to monitor. It communicates with the Wazuh server, sending data in near real-time through an encrypted and authenticated channel.

## Pre-requisite
-  [Wazuh Agent Manager](https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-windows.html)
-  Wazuh Server
-  Make sure wazuh agent & server are in same network

To Deploy agent type followings commands in terminal, ``` /var/ossec/bin/manage_agents ``` and select ``` A ``` to add new agent.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/9b3c0ca0-a57a-41a5-879a-8aa9058d4c80" width="400px" height="250px"><br>Figure (1) </p>

Add device name & ip address to add agent. After adding it type ``` Y ``` to confirm.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/2bff8296-b2a9-4cbd-b6fc-13906b51db62" width="400px" height="250px"><br>Figure (2) </p>

We need to generate authentication keys select ``` E ``` and type agent id im this case ``` 003 ``` and we got a keys & copies it.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/13bdbdad-29b7-42d5-945b-3dfd62eca408" width="400px" height="250px"><br>Figure (3) </p>

We need to install Wazuh Agent Manager by clicking next with easily. After installed it add Wazuh Server IP & authentication keys and click save.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/681d7f09-831b-4ff0-ad52-d51afb198b77" width="400px" height="250px"><br>Figure (4) </p>

Click on Manage & start Wazuh Agent Manager to parse log data.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/6e9f0795-5296-4f31-b924-6825c38ef8b2" width="400px" height="250px"><br>Figure (5) </p>

In our Wazuh Server, new agents was deployed.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/a24becbe-90d3-4617-8e5f-c1b079ef2ba9" width="500px" height="300px"><br>Figure (6) </p>

In this tutorial, Windows Wazuh Agent Deployment is demostrated. Do more Practice and Expert it!. <br>
**3/27/2024** <br>
Contributed By - Jord@n
