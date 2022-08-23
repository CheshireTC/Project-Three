# **Defensive Report**

## **__Table of Contents__**

* Network Topology
* Description of Targets
* Monitoring the Targets
* Patterns of Traffic & Behavior
* Suggestions for Going Further


### **__Network Topology:__**
---------------------

The following machines were identified on the network:

### __Azure VM__:

Operating System: Windows
Purpose: Hosts the to Other VMs
IP Address: 192.168.1.1 (10.0.0.27)

### __ELK VM__:

Operating System: Linux
Purpose: Used to view created alerts and reports from targets
IP Address: 192.168.1.100

### __Kali VM__:

Operating System: Linux (Kali)
Purpose: Used to attack the targets on the network
IP Address: 192.168.1.90

### __Target 1 VM__:

Operating System: Linux
Purpose: Used to host the vulnerable wordpress server for us to attack
IP Address: 192.168.1.110

### __Target 2 VM__:

Operating System: Linux
Purpose: Optional Attack Target
IP Address: 192.168.1.115

### __Capstone VM__:

Operating System: Linux
Purpose: Used to test alerts and log gathering from the ELK machine
IP Address: 192.168.1.105


### **__Description of Targets:__**
------------------------------

The target of this attack was: Target 1 (192.168.1.110).
Target 1 is an Apache web server and has SSH enabled, so ports 80 and 22 are possible ports of entry for attackers. As such, the following alerts have been implemented:

Monitoring the Targets
Traffic to these services should be carefully monitored. To this end, we have implemented the alerts below:

### __Excessive HTTP Errors__:

Excessive HTTP Errors is implemented as follows:

Metric: Top 5 http response status codes

Threshold: count of 400 over 5 minutes

Vulnerability Mitigated: Brute Forces

Reliability: Medium to High depending on size of company


### __HTTP Request Size Monitor__:

HTTP Request Size Monitor is implemented as follows:

Metric: Total of all http request bytes on all documents

Threshold: 3500 bytes for the last minute

Vulnerability Mitigated: DoS Attacks

Reliability: High


### __CPU Usage Monitor__:

CPU Usage Monitor is implemented as follows:

Metric: CPU Usage percentage on all documents

Threshold: Over 0.5 for the last 5 minutes.

Vulnerability Mitigated: Malicious Script

Reliability: Low