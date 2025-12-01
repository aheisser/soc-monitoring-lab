Atomic Red Team Tests (Attacker Simulation)

This document tracks the attacker simulation techniques executed in the SOC Monitoring Lab using Atomic Red Team. These controlled simulations help verify that Wazuh correctly captures, logs, and alerts on malicious behavior.

These tests were run only inside a contained lab environment, never on production systems.

---

Purpose of These Tests

- Validate detection coverage for Windows endpoints  
- Produce real-world attacker-like behavior  
- Generate logs for SIEM analysis  
- Map observed events to MITRE ATT&CK techniques  
- Practice SOC-style alert investigation  


Test Environment

- Target Host: Windows 10 VM  
- Privileges: Local Administrator  
- Tools Used: 
  - PowerShell  
  - Atomic Red Team (manual execution of test commands)  
- Logging Sources: 
  - Windows Security Logs  
  - PowerShell logs  
  - Sysmon (if enabled in future)  
  - Wazuh Agent forwarded logs  


 Executed Atomic Tests

Atomic Red Team Tests Performed in SOC Monitoring Lab

Below are all simulated adversary techniques executed in this project, including descriptions, detection logic, and artifacts observed. These tests validated the Wazuh SIEM, Linux agent, Windows agent, and Sysmon logging.


T1110 – Brute Force (SSH Authentication Failures)

Description:  
Simulated password-guessing attacks by repeatedly attempting SSH login with incorrect credentials to generate authentication failures.

Execution:  
Manual SSH attempts:  
ssh root@3.22.187.36  
Repeated with wrong passwords.

Detection:  
Wazuh Rule 5716 – sshd: authentication failed  
Custom Local Rule 100001 using <if_sid>5716</if_sid> and <srcip>1.1.1.1</srcip>  
Grouped under authentication_failed and pci_dss categories.

Artifacts Observed:  
/var/log/auth.log:  
Failed password for root from 3.22.187.36  
Wazuh alert (level 5) triggered from local rule  
Alerts visible on Wazuh dashboard under Authentication Failures


T1078 – Valid Accounts (Successful SSH Login)

Description:  
Verified detection of legitimate SSH logins to ensure baseline account monitoring.

Execution:  
SSH login from Mac terminal using valid credentials.

Detection:  
Wazuh Rule 5501 – successful SSH login  
Source IP and user correlation  
Agent forwarded auth logs in real time

Artifacts Observed:  
/var/log/auth.log:  
Accepted password for ubuntu from 3.22.187.36  
Wazuh alert: User logged in  
Visualized session events in manager dashboard


T1059 – Command Execution (Linux Shell Activity)

Description:  
Generated system command logs by executing administrative and common Linux commands.

Execution Examples:  
sudo apt update  
systemctl restart wazuh-agent  
nano /var/ossec/etc/rules/local_rules.xml

Detection:  
Sysmon for Linux (if installed)  
Wazuh command monitoring module  
Linux audit subsystem

Artifacts Observed:  
/var/log/syslog command execution logs  
Wazuh alerts for configuration file modifications  
File integrity monitoring (FIM) triggered when editing Wazuh rules


T1105 – Command and Control: Remote File Copy (Agent Registration)

Description:  
Simulated remote communication by installing and registering Linux and Windows agents with the Wazuh manager.

Execution:  
Installed Wazuh Linux agent  
Installed Wazuh Windows agent  
Registered Windows agent using the authentication key  
Manager–agent handshake validated

Detection:  
Wazuh agent connection logs  
/var/ossec/logs/authd.log – agent key requests  
/var/ossec/logs/ossec.log – connection status

Artifacts Observed:  
agentd: INFO: Using authentication key  
agentd: Agent started and connected  
Wazuh dashboard: Agent status changed to Active


T1082 – System Information Discovery (Windows and Linux)

Description:  
Validated system discovery logs generated automatically during Windows agent and Sysmon installation.

Execution:  
Triggered automatically through Wazuh inventory module and Windows event generation.

Detection:  
Wazuh decoders for Windows event logs  
Sysmon Event ID 1 (process creation), Event ID 3 (network connections)  
Windows Event ID 4688 (process creation)

Artifacts Observed:  
Wazuh inventory details populated (OS, hostname, architecture)  
Sysmon logs showing initial process activity  
Windows Security logs visible under Wazuh


Below is the system information enumeration executed on the Windows VM:

![System Info](../screenshots/Powershell-systeminfo.png)


T1547 – Persistence via Service Installation (Windows Agent Install)

Description:  
Installing Wazuh agent creates a persistent Windows Service, similar to how adversaries maintain persistence.

Execution:  
Installed Wazuh Windows agent MSI package.

Detection:  
Windows Event ID 7045 – A new service was installed  
Sysmon Event IDs 12–14 (registry modifications)  
Wazuh rules detecting new service installs and registry changes

Artifacts Observed:  
A service was installed: Wazuh Agent  
Registry keys created:  
HKLM\SYSTEM\CurrentControlSet\Services\Wazuh  
Service executable logged in Sysmon process creation


T1566 – Phishing (Simulated Log Visibility Check)

Description:  
No malicious email payload was executed, but general network and authentication behavior validated visibility for phishing-related actions.

Execution:  
Environmental user activity (SSH, commands, agent install) simulated typical reconnaissance and interaction patterns.

Detection:  
Wazuh event correlation  
Linux and Windows endpoint logs

Artifacts Observed:  
Session events, command logs, service installs, and login activity  
Baseline visibility confirmed for future phishing simulations


---

T1087 – Account Discovery

Whoami privileges enumeration:

![Whoami Privileges](../screenshots/Powershell-whoami-privledges.png)

Local group enumeration:

![Local Groups](../screenshots/powershell-local-groups.png)

---

T1057 – Process Discovery

Process list captured during reconnaissance:

![Processes](../screenshots/Powershell-process-list.png)

---

T1518 – Software Discovery

![Installed Software](../screenshots/powershell-installed-software.png)

---

T1069.001 – Permission Groups Discovery (Firewall Rules)

![Firewall Rules](../screenshots/powershell-firewall-rules.png)



Summary

This lab successfully tested:

Authentication failure detection  
Valid login detection  
Linux command execution monitoring  
Agent to Manager authentication and registration  
Windows service persistence detection  
Sysmon-enhanced endpoint visibility  
Log collection, parsing, alerting, and correlation through Wazuh

These tests confirm that the environment is fully operational as a SOC monitoring and detection lab.




