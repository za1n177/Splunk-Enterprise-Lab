## Phase 1 – Splunk Pre-check & Download

### Objective
Prepare Ubuntu Server for Splunk Enterprise installation and validate system readiness.

### Pre-checks Performed
- Verified OS: Ubuntu 24.04 LTS
- Verified CPU architecture: x86_64
- Verified available disk space and memory
- Confirmed internet connectivity and DNS resolution

### Download Method
Direct `wget` download from Splunk failed due to authentication requirements (expected behavior).
Splunk Enterprise was manually downloaded via browser and securely transferred to the Ubuntu server using SCP.

### Outcome
- Splunk Enterprise installer successfully staged on Ubuntu server
- System ready for Splunk installation (Phase 2)
