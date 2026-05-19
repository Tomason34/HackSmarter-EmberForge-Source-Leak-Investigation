⚠️ Disclosure: This write‑up was created with AI assistance, but I did all the actual lab work.

# HackSmarter – EmberForge Source Leak Investigation

##  Overview
This investigation analyzes a simulated enterprise breach involving source code theft from EmberForge.  
Using Splunk log analysis, the attacker’s activity was reconstructed from initial execution to data exfiltration and persistence.

---

##  Investigation Phases

### Phase 1 – Initial Execution
- Suspicious execution:

rundll32.exe D:\review.dll,StartW

- Malicious DLL executed from non-standard drive.
- SHA256:

0BB68E54629555FB9F70FB8D7B95FE1A5F987EEEEF57DE0A2671EEB14063CED1


---

### Phase 2 – Command & Control
- Outbound connections:

104.21.30.237:443

- Domain observed:

cdn.cloud-endpoint.net


---

### Phase 3 – Credential Access
- LSASS dump created:

C:\Windows\System32\lsass.dmp

- Dump performed by:

C:\Users\Public\update.exe


---

### Phase 4 – Privilege Escalation
- UAC bypass via:

fodhelper.exe

- Registry modification:

HKCU\Software\Classes\ms-settings\shell\open\command


---

### Phase 5 – Data Staging & Exfiltration
- Staged archive:

gamedev.zip

- Exfiltration tool:

rclone.exe

- Cloud destination:

MEGA

- Credentials discovered in logs:

jwilson.vhr@proton.me


---

### Phase 6 – Persistence
- Scheduled task:

WindowsUpdate

- Backdoor account:

svc_backup

- Password:

P@ssw0rd123!


---

### Phase 7 – Anti-Forensics
- Security logs cleared
- Event ID:

1102


---

##  Blast Radius
- Total compromised hosts:

3


---

##  Tools Used
- Splunk (SPL queries)
- Windows Event Logs
- Sysmon Process Creation logs
- Network telemetry analysis

---

##  Skills Demonstrated
- Log analysis
- Threat hunting
- Process lineage investigation
- Lateral movement detection
- Data exfiltration tracing
- Persistence identification
- Incident response reporting

---

##  Outcome
Successfully reconstructed attacker activity from execution through exfiltration and persistence, identifying full attack chain and indicators of compromise.

---

 Lab completed via HackSmarter.org
