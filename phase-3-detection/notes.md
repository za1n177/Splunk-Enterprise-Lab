# Phase 3 – Detection (Privilege Escalation)

## Objective
Detect and analyze Linux privilege escalation activity using sudo events.

---

## Step 2 – Sudo Success & Root Session Detection

### Data Source
- Index: main
- Sourcetype: journald
- Host: Ubuntu-Server

---

### Detection Use Cases

#### 1. Successful sudo session
SPL:
index=main sourcetype=journald "pam_unix(sudo:session)" "session opened"

yaml
Copy code

Result:
- Detected successful privilege escalation to root
- Example event:
  pam_unix(sudo:session): session opened for user root(uid=0)

Screenshot:
- P3-04-sudo-success-events.png

---

#### 2. Sudo usage by user
SPL:
index=main sourcetype=journald ("sudo:" OR "pam_unix(sudo")
| stats count by user host
| sort -count

yaml
Copy code

Screenshot:
- P3-05-sudo-success-by-user.png

---

#### 3. Root session opened
SPL:
index=main sourcetype=journald "pam_unix(sudo:session)" "session opened for user root"

yaml
Copy code

Screenshot:
- P3-06-root-session-opened.png

---

## Security Relevance
- Identifies privilege escalation
- Detects unauthorized root access
- Useful for SOC monitoring, IR, and audit trails

---

## Notes
Initial absence of events was due to lack of successful sudo executions.
Once sudo was successfully executed, detection queries returned valid results.
