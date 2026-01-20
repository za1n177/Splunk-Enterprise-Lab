Phase 2 – Linux Authentication & System Activity Monitoring (journald)
Objective

Validate ingestion and analysis of Linux authentication, session, and system service events using Systemd Journald Input in Splunk Enterprise.

This phase focuses on security-relevant host telemetry commonly used in SOC investigations.

Data Source

Input Type: Systemd Journald Input

Index: main

Sourcetype: journald

Host: Ubuntu-Server

Log Source: /run/log/journal (systemd journal)

Key Validations
1. Journald Logs Successfully Indexed

SPL

index=main sourcetype=journald


✔️ Confirms systemd logs are ingested and searchable

2. Authentication Events (User Sessions)

SPL

index=main sourcetype=journald "pam_unix"


Observed Events

User session opened

UID / EUID tracking

TTY session visibility

✔️ Validates Linux login/session monitoring

3. Sudo Authentication Failures

SPL

index=main sourcetype=journald ("authentication failure" OR "sudo")


Observed Events

pam_unix(sudo:auth): authentication failure

User identity, terminal, and target command captured

✔️ Demonstrates privilege escalation monitoring

4. Login Activity Summary

SPL

index=main sourcetype=journald ("authentication failure" OR "session opened")
| stats count by _raw


✔️ Confirms ability to summarize authentication behavior

5. Systemd Service Activity Overview

SPL

index=main sourcetype=journald SYSTEMD_UNIT=*
| stats count by SYSTEMD_UNIT
| sort -count


✔️ Shows operational awareness of system services

Security Takeaways

Journald provides richer context than traditional syslog

PAM events are critical for:

brute-force detection

privilege escalation investigations

insider threat analysis

SPL can quickly pivot from raw logs → security insight
