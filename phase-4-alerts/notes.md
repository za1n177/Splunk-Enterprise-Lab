# Phase 4 – Security Alerts (Splunk SIEM)

## Objective
Configure security alerts in Splunk to detect suspicious Linux authentication activity and privilege escalation attempts using systemd journal logs.

---

## Alerts Implemented

### 1. Linux Multiple Authentication Failures
**Purpose:**  
Detect repeated authentication failures which may indicate brute-force or credential stuffing attempts.

**Search Logic:**
```spl
index=main sourcetype=journald "authentication failure"
| stats count by host user
| where count > 0
Trigger Type: Scheduled (Hourly)
Action: Log Event

📸 Screenshot: P4-01-auth-failure-alert.png

2. Linux Brute Force Authentication Attempt
Purpose:
Identify excessive sudo authentication failures and unauthorized privilege attempts.

Search Logic:

spl
Copy code
index=main sourcetype=journald ("sudo" OR "user NOT in sudoers")
Trigger Type: Scheduled (Hourly)
Action: Log Event

📸 Screenshot: P4-02-bruteforce-auth-alert.png

3. Linux Root Privilege Escalation
Purpose:
Detect successful root privilege escalation via sudo session creation.

Search Logic:

spl
Copy code
index=main sourcetype=journald "session opened for user root"
Trigger Type: Scheduled (Hourly)
Action: Log Event

📸 Screenshot: P4-03-root-privilege-escalation-alert.png

Skills Demonstrated
Splunk SPL (Search Processing Language)

Linux authentication & sudo log analysis

SOC alert logic and thresholds

Privilege escalation detection

Security monitoring & incident detection

