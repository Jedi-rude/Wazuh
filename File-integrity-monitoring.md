# File Integrity Monitoring (FIM)

File Integrity Monitoring (FIM) is a security process used to monitor the integrity of system and application files. FIM is an important security defense layer for any organization monitoring sensitive assets.
It provides protection for sensitive data, application, and device files by monitoring, routinely scanning, and verifying their integrity. It helps organizations detect changes to critical files on their systems which reduces the risk of data being stolen or compromised.
This process can save time and money in lost productivity, lost revenue, reputation damage, and legal and regulatory compliance penalties.

## Pre-requisite
-  [Wazuh Agent Manager](https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-windows.html)
-  Wazuh Server
-  Make sure wazuh agent & server are in same network

## wazuh-agent manager configurations

``` <directories check_all="yes" realtime="yes" report_changes="yes">FILEPATH/OF/MONITORED/DIRECTORY</directories> ```

- When you configure the FIM module to monitor specific files and directories, it records the metadata of the files and monitors them. The directories option supports several attributes.

- The report_changes attribute allows the FIM module to report the exact content changed in a text file. This records the text added to or deleted from a monitored file. The allowed values for this attribute are yes and no.

- The realtime attribute enables real-time/continuous monitoring of directories on Windows and Linux endpoints only. The allowed values for the realtime attribute are yes and no, and it only works with directories, not individual files. 

- FILEPATH/OF/MONITORED/DIRECTORY which is directory you want to monitor.

add above directories attribute to wazuh-agent manager configurations files which located under followings path.
```
    Linux: /var/ossec/etc/ossec.conf

    Windows: C:\Program Files (x86)\ossec-agent\ossec.conf
```

<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/bbd66db3-2f5e-4f1f-9959-a7f1edacd7d9" width="500px" height="250px"><br>Figure (1) wazuh-agent manager configurations </p>

When some changes made on monitored directory alerts are shown in dashboards under agents\Integrity Monitoring tab.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/193d5386-d558-4122-b614-cfebc2c2a84f" width="500px" height="250px"><br>Figure (2) </p>

 When some changes made on monitored directory alerts are shown in under agents\Events tab.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/457642f3-da93-42bc-81ca-776ebe731a67" width="500" height="250px"><br>Figure (3) </p>

There are hashes of monitored files with different hashing algorithms. 
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/12722331-95d5-4d4a-a3ba-3742062d836a" width="500px" height="250px"><br>Figure (4) </p>

When files removing made on monitored directory alerts are shown in dashboards under agents\Integrity Monitoring tab.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/8497d076-a320-40d8-a8e8-ef9273fdba67" width="500px" height="250px"><br>Figure (5) </p>

Details analysis of File Integrity Monitoring.
<p align="center"><img src="https://github.com/AungZayMyo/Wazuh/assets/154745254/f44b7025-7d61-4ffa-a3bb-b8e33e79667e" width="500px" height="250px"><br>Figure (6) </p>

In this tutorial, File Integrity Monitoring in Windows Wazuh Agent is demostrated. Do more Practice and Expert it!. <br>
**3/29/2024** <br>
Contributed By - Jord@n
