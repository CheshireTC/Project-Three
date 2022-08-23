# Defensive Report

## Table of Contents

..* Network Topology
..* Description of Targets
..* Monitoring the Targets
..* Patterns of Traffic & Behavior
..* Suggestions for Going Further


### Network Topology
The following machines were identified on the network:

#### Azure VM

Operating System: Windows
Purpose: Hosts the to Other VMs
IP Address: 192.168.1.1 (10.0.0.27)

#### ELK VM

Operating System: Linux
Purpose: Used to view created alerts and reports from targets
IP Address: 192.168.1.100

#### Kali VM

Operating System: Linux (Kali)
Purpose: Used to attack the targets on the network
IP Address: 192.168.1.90

#### Target 1 VM

Operating System: Linux
Purpose: Used to host the vulnerable wordpress server for us to attack
IP Address: 192.168.1.110

#### Target 2 VM

Operating System: Linux
Purpose: Optional Attack Target
IP Address: 192.168.1.115

#### Capstone VM

Operating System: Linux
Purpose: Used to test alerts and log gathering from the ELK machine
IP Address: 192.168.1.105


### Description of Targets:

The target of this attack was: Target 1 (192.168.1.110).
Target 1 is an Apache web server and has SSH enabled, so ports 80 and 22 are possible ports of entry for attackers. As such, the following alerts have been implemented:

Monitoring the Targets
Traffic to these services should be carefully monitored. To this end, we have implemented the alerts below:

#### Excessive HTTP Errors:

Excessive HTTP Errors is implemented as follows:

Metric: Top 5 http response status codes

Threshold: count of 400 over 5 minutes

Vulnerability Mitigated: Brute Forces

Reliability: Medium to High depending on size of company


#### HTTP Request Size Monitor

HTTP Request Size Monitor is implemented as follows:

Metric: Total of all http request bytes on all documents

Threshold: 3500 bytes for the last minute

Vulnerability Mitigated: DoS Attacks

Reliability: High


#### CPU Usage Monitor

CPU Usage Monitor is implemented as follows:

Metric: CPU Usage percentage on all documents

Threshold: Over 0.5 for the last 5 minutes.

Vulnerability Mitigated: Malicious Script

Reliability: Low