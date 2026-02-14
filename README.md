# Building a SOC and Honeynet in Azure with Live Traffic

## Introduction

In this project, I created a mini honeynet in Azure and ingest various log from various sources into a Log Analytics Workspace, and then used Microsoft Sentinel and KQL to create attack maps, trigger alerts, and create incidents. I also measured some security metrics before and 24 hours after implementing and applying security controls to harden the environment. There security metrics are as follow:
  - SecurityEvent (Windows Event Logs)
  - SecurityAlert (Log Analytic Alerts Triggered)
  - SecurityIncident (Incidents created by Sentinel)
  - NTANetAnalytics (Malicious Flows allowed into our honeynet)

## Components
Architecture of the mini honeynet is consist of the following components:
  - Virtual Network (VNet)
  - Network Security Group (NSG)
  - Windows virtual machine
  - Log Analytics Workspace
  - Microsoft Sentinel
  - Azure Key Vault
  - Azure Storage Account
   
## Architecture Before Hardening with Security Controls


All resouces were originally deployed exposed to the internet with all traffics allowed. The virtual machine had its Network Security Group and host firewall wide open.

### Attack Maps
![Attack Maps](https://github.com/kvang138/Azure-SOC-and-Honeynet/blob/main/Screenshots/Azure-SOC-and-Honeynet%20Attack%20Maps.png)

```*** The 191,000 failed login attempts and others can likely be attributed to an automated tool such as Hydra using the rockyou.txt wordlist. ***```

```On a low-latency 1 Gbps connection, Hydra has been observed to achieve approximately 1,114 login attempts per minute—or roughly 66,840 attempts per hour—against RDP.```

The table below shows the metrics that were measured before the environment was hardened.

### Metrics Before Hardening

| Metric           | Count
|----------------- | -----
| SecurityEvent    |370630
| SecurityAlert    |36
| SecurityIncident |368
| NTANetAnalytics  |1388

## Architecture After Hardening with Security Controls
All deployed resources are now hardened with security controls. The Network Security Group were hardened by blocking all traffics with the expection of the administrator workstation.

```All map queries returned no results, as there were no instances of malicious activity in the 24-hour period after hardening the environment.```

The table below shows the metrics that were measured in the 24-hour period right after hardening the environment.

### Metrics After Hardening
| Metric           | Count
|----------------- | -----
| SecurityEvent    |8898
| SecurityAlert    |0
| SecurityIncident |0
| NTANetAnalytics  |0

## Conclusion
It worth noting that the number of event and incident were drastically reduced after security controls were implemented and applied, demostrating their effectiveness in preventing unwanted cyberthreats and incidents.

   
 
