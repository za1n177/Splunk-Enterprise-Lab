## Phase 1 – Splunk Enterprise Installation & Access

### Objective
Install and validate Splunk Enterprise on Ubuntu Server and enable secure web access from host machine.

### Environment
- Ubuntu Server 24.04 LTS (VirtualBox)
- Splunk Enterprise 10.2
- Network: Host-only (192.168.56.0/24) with port forwarding

### Key Steps
- Verified system resources and network interfaces
- Downloaded Splunk Enterprise via official Splunk repository
- Extracted Splunk to /opt/splunk
- Started Splunk and accepted license
- Opened firewall port 8000 using UFW
- Verified Splunk web service listening on TCP 8000
- Accessed Splunk Web UI via port forwarding (127.0.0.1:8000)
- Logged in as admin and validated dashboard access

### Outcome
Splunk Enterprise successfully installed, running, and accessible from host browser.
