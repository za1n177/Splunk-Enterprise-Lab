# Phase 3 – Step 1: Failed Authentication Detection

## Objective
Detect repeated Linux authentication failures using Splunk to identify potential brute-force or misuse activity.

## Detection Logic
- Source: systemd journald
- Sourcetype: journald
- Index: main

## SPL Queries

### View Authentication Failures
```spl
index=main sourcetype=journald "authentication failure"
Count Failures by User
spl
Copy code
index=main sourcetype=journald "authentication failure"
| stats count by host user
| sort -count
Threshold-Based Detection
spl
Copy code
index=main sourcetype=journald "authentication failure"
| stats count by host user
| where count >= 2
| sort -count
Outcome
Successfully identified failed authentication attempts

Demonstrated SOC-style threshold detection

Ready for alert creation in next phase
