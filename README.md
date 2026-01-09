# Building a SOC and Honeynet in Azure with live traffic

## Introduction

In this project, I created a mini honeynet in Azure and ingest various log from various sources into a Log Analytics Workspace, and then used Microsoft Sentinel and KQL to attack maps, trigger alerts, and create incidents.
I also measured some security metrics before and 24 hours after implementing and applying security controls to harden the environment. There security metrics are as follow:
  SecurityEvent (Windows Event Logs)
  SecurityAlert (Log Analytic Alerts Triggered)
  SecurityIncident (Incidents created by Sentinel)
  NATAnalyic (Malicious Flows allowed into our honeynet)

## 

 ## Architecture before hardening with security controls


All inbound connections are allowed.
 ## Architecture after hardening with security controls

 Architecture of the mini honeynet is consist of the following components:
   Virtual Network (VNet)
   Network Security Group (NSG)
   Windows virtual machine
   Log Analytics Workspace
   Microsoft Sentinel
   Azure Key Vault
   Azure Storage Account


   
 
