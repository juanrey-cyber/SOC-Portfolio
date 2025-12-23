# SOC Case 05 — Persistence via Scheduled Tasks and Registry

## Overview

This case documents the investigation of persistence mechanisms used by attackers to maintain access to a compromised system. Persistence allows a threat actor to regain access after reboots or user logouts and is a critical phase of the attack lifecycle. This investigation focuses on two common persistence techniques: Scheduled Tasks and Registry-based autorun entries.

---

## Environment

- Operating System: Windows
- Investigation Context: SOC alert triage and post-compromise analysis
- Log Sources:
  - Windows Security Event Logs
  - Task Scheduler Operational Logs
  - Registry autorun locations (conceptual analysis)

---

## What Is Persistence (Explained Simply)

Persistence refers to techniques attackers use to ensure their malicious code continues to run over time. Even if the system is rebooted or the user logs out, persistence mechanisms allow the attacker to automatically re-execute malware.

Common persistence methods include:
- Scheduled Tasks
- Registry Run Keys
- Services
- Startup folders

This case focuses on Scheduled Tasks and Registry Run Keys due to their frequent use in real-world attacks.

---

## Detection

Suspicious activity was identified based on the creation of new scheduled tasks and registry modifications without a clear administrative justification.

Indicators included:
- Scheduled tasks executing PowerShell or script files
- Tasks running at logon or system startup
- Registry Run keys pointing to scripts or executables in non-standard directories
- Use of obfuscated or encoded commands
- Execution under non-administrative user context

---

## Investigation

### Scheduled Tasks Analysis

Attackers often create scheduled tasks that execute malicious scripts at regular intervals or upon user logon.

Key investigation steps:
- Identify recently created scheduled tasks
- Review task triggers (logon, startup, time-based)
- Analyze task actions (PowerShell, cmd.exe, scripts)
- Determine execution frequency and user context

Scheduled tasks that execute PowerShell with hidden windows or encoded commands are considered highly suspicious.

---

### Registry Persistence Analysis

Another common persistence technique involves modifying Windows Registry autorun keys.

Typical autorun locations include:
- HKCU\Software\Microsoft\Windows\CurrentVersion\Run
- HKLM\Software\Microsoft\Windows\CurrentVersion\Run

Indicators of malicious registry persistence:
- Executables stored in TEMP or AppData directories
- Obfuscated PowerShell commands in registry values
- Registry entries created shortly after suspicious activity
- Lack of associated legitimate software installation

---

## Indicators of Compromise (IOCs)

Potential indicators observed during this investigation:
- New scheduled tasks with suspicious names or triggers
- PowerShell execution via scheduled tasks
- Registry Run keys pointing to unknown scripts or binaries
- Persistence mechanisms created outside business hours

---

## MITRE ATT&CK Mapping

The activity observed maps to the following MITRE ATT&CK techniques:

- T1053 — Scheduled Task / Job
- T1547.001 — Registry Run Keys / Startup Folder
- T1059.001 — Command and Scripting Interpreter: PowerShell
- T1027 — Obfuscated / Encrypted Payloads

---

## Severity and Confidence Assessment

**Severity: High**  
**Confidence: High**

Rationale:
- Persistence mechanisms indicate post-compromise activity
- Scheduled tasks and registry autoruns are well-known attacker techniques
- Lack of legitimate administrative justification
- Potential for continued system compromise and lateral movement

---

## Response and Next Steps

Recommended SOC actions:
1. Disable and remove malicious scheduled tasks
2. Remove malicious registry autorun entries
3. Identify the initial infection vector
4. Inspect the host for additional persistence mechanisms
5. Review network activity for command-and-control communication
6. Escalate to Incident Response for containment and remediation

---

## Analyst Conclusion

The presence of unauthorized scheduled tasks and registry-based autorun entries strongly suggests an attempt to maintain persistence following an initial compromise. This behavior represents a high-risk security incident requiring immediate remediation and further investigation to prevent reinfection and lateral movement.
