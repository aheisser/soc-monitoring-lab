Log Analysis Workflow

This document explains the SOC-style analysis process used during the project to investigate alerts and suspicious activity in Wazuh.

---

Purpose

- Practice real SOC analyst investigation  
- Correlate Windows and network logs  
- Build timelines of activity  
- Interpret alert details  
- Make conclusions and recommend actions  

---

Step 1 — Review the Alert

For each alert in Wazuh:

- Rule ID  
- Description  
- Severity  
- Timestamp  
- Source user  
- Source IP  
- Affected host  

This becomes the starting point for the investigation.

Log Analysis Workflow

Step 1 — Review the Alert

Example alert displayed in Wazuh MITRE dashboard:

![MITRE Dashboard](../screenshots/wazuh-mitre-dashboard.png)

Another example dashboard view:

![MITRE Dashboard 2](../screenshots/wazuh-mitre-dashboard-2.png)


---

Step 2 — Pivot to Raw Logs

Use the Wazuh Dashboard to view logs related to the alert:

Common log sources used:
- Windows Security Logs
  - Logon/logoff (4624, 4625)
  - Process creation (4688)
  - PowerShell logs (4104)
- DNS Logs 
- HTTP Logs  
- FTP Logs  
- Tunnel / VPN activity  
- DHCP events

Pivot questions:
- What happened before the alert?  
- What happened after?  
- Is this normal behavior for this host or user? 

---

Step 3 — Protocol-Specific Checks

DNS
- Suspicious domains  
- High-frequency queries  
- Possible beaconing  

HTTP
- Requests to unknown or malicious endpoints  
- Suspicious user agents
FTP
- Login failures  
- Unusual file transfers  

Tunnel/VPN
- Unexpected tunnel creation  
- Unknown endpoints  

SMTP
- Outbound mail attempts  
- Suspicious sender accounts  

DHCP
- IP address changes  
- New devices appearing  

---

Step 4 — Build a Timeline

Combine logs into a timeline:
T0 - User login event (4624)
T1 - PowerShell executed suspicious command (4104)
T2 - DNS Query to suspicious domain
T3 - Outbound connection attempt
T4 - Wazuh alert triggered
	- This helps determine if the activity is malicious or benign.
—-

Step - 5 - Write Investigation Summary

Template (Used in this lab):

Alert:
Initial Finding:
Related Logs:
Analysis:
Conclusion: (Benign / Suspicious / Needs Review)
Recommended Action:


---

Benefits

This approach builds skills relevant to:

- SOC Tier 1 analysis  
- Threat detection  
- Incident response  
- Log correlation  
- MITRE technique identification  

