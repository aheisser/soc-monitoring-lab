Wazuh Manager Setup (Ubuntu Server)

This document describes how the Wazuh manager stack was installed and configured.


1. Update Ubuntu Server

bash
sudo apt update && sudo apt upgrade -y

Service Verification:
 
Service Status:

Verified running services:
- wazuh-manager: active (running)
- wazuh-indexer: active (running)
- wazuh-dashboard: active (running)

Commands used:
sudo systemctl status wazuh-manager
sudo systemctl status wazuh-indexer
sudo systemctl status wazuh-dashboard

Dashboard Access (Completed):

Accessed Wazuh dashboard at:
https://3.22.187.36

Logged in using admin account created during installation.
Dashboard successfully displayed:
- Agents page
- Security events
- Welcome panel

