Lab Architecture

This document explains the layout of the SOC Monitoring VM environment.

Components

1. Wazuh Manager Stack (Ubuntu Server)
- Wazuh Manager  
- Wazuh Indexer  
- Wazuh Dashboard  
- Receives logs, runs detection rules, displays alerts

2. Windows 10 VM
- Wazuh agent installed  
- Generates:
  - Windows Security Logs
  - Process creation events
  - Event logs from Atomic Red Team simulations

3. (Optional) Linux Endpoint(s)
- Wazuh Linux agent  
- Additional logs for multi-host detection scenarios

Network Flow Diagram:

[Local Computer] ---- HTTPS ----> [Wazuh Dashboard / Ubuntu Cloud VM] | +---- SSH ----> Ubuntu Server (Manager)
Windows 10 VM ---- TCP/1514 ----> Wazuh Manager (Log Ingestion)

Ports Used:
- TCP 1514/1515 — Wazuh agent → Manager  
- TCP 22 — SSH  
- TCP 443 / 5601 — Dashboard access  

 Purpose of This Lab:
- Build real SIEM hands-on experience  
- Analyze endpoint & network logs  
- Simulate attacker techniques  
- Practice SOC-style alert triage  


