# SOC Cases (Portfolio)

This folder contains hands-on SOC investigations I performed in a controlled lab environment. Each case includes: timeline, log evidence, MITRE ATT&CK mapping, severity/confidence decision-making, and remediation recommendations.

## Case Index

| Case | Title | Platform | Core Skills | Tools | MITRE Focus | Outcome |
|------|-------|----------|------------|-------|------------|---------|
| 01 | SSH Brute Force Detection | Linux | Log triage, pattern detection | auth.log, grep | T1110 | Identified repeated failed SSH attempts and documented indicators |
| 02 | SSH Brute Force Decision Analysis | Linux | Severity/Confidence, escalation logic | auth.log | T1110 | Determined risk level and recommended monitoring + controls |
| 03 | Windows Suspicious PowerShell Activity | Windows | Scripting telemetry triage | Event logs, PowerShell | T1059 | Evaluated suspicious PowerShell execution and response steps |
| 04 | (Add your Case 04 title) | (Linux/Windows) | (Key skills) | (Tools) | (MITRE) | (Outcome) |
| 05 | (Add your Case 05 title) | (Linux/Windows) | (Key skills) | (Tools) | (MITRE) | (Outcome) |
| 06 | (Add your Case 06 title) | (Linux/Windows) | (Key skills) | (Tools) | (MITRE) | (Outcome) |
| 07 | (Add your Case 07 title) | (Linux/Windows) | (Key skills) | (Tools) | (MITRE) | (Outcome) |
| 08 | Wazuh SSH Brute Force Detection | Linux | SIEM alerting, detection validation | Wazuh | T1110 | Verified SIEM detection of SSH brute force attempts |
| 09 | Linux Privilege Escalation & Docker Activity | Linux | Privilege audit, service/container activity | auth.log, Docker | T1548.003, T1610 | Confirmed authorized activity, documented impact + mitigations |

## How I Work (SOC Method)
1. Confirm scope (host/user/time).
2. Collect evidence (logs/artifacts).
3. Build a timeline.
4. Map to MITRE ATT&CK.
5. Assign severity + confidence (with reasoning).
6. Decide: close vs escalate (and why).
7. Recommend remediation and prevention.
