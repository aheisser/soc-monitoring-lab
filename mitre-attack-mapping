MITRE ATT&CK Mapping

This document maps Atomic Red Team tests and Wazuh detections to MITRE ATT&CK techniques.

---

 Purpose

- Demonstrate detection coverage  
- Align log events and alerts to ATT&CK framework  
- Identify potential gaps  

---

Mapping Table

| Technique ID | Technique Name                  | Source               | Host        | Wazuh Rule ID | Notes |
|--------------|----------------------------------|----------------------|-------------|----------------|-------|
| T1082        | System Information Discovery     | Atomic Red Team      | Win10-lab   | 500002         | System info commands executed |
| T1059        | Command & Scripting Interpreter  | Atomic Red Team      | Win10-lab   | 510001         | Suspicious PowerShell execution |
| T1003        | Credential Dumping (Simulated)   | Atomic Red Team      | Win10-lab   | 580050         | Elevated access attempt |
| T1046        | Network Service Scanning         | Manual (Nmap)        | Ubuntu VM   | 571000         | Detected port scanning activity |

---

 What This Shows

- Wazuh detected key attacker behaviors  
- Endpoint visibility is strong for Windows VM  
- Additional coverage can be added:
  - Persistence techniques  
  - Lateral movement  
  - Privilege escalation  

---

 MITRE ATT&CK Dashboard Evidence

![MITRE Dashboard](../screenshots/wazuh-mitre-dashboard.png)
![MITRE Dashboard 2](../screenshots/wazuh-mitre-dashboard-2.png)


Future Mapping

As more Atomic tests are added, update this table to show evolving coverage.
