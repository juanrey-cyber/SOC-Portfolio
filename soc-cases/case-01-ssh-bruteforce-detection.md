# SOC Case 01 – SSH Brute Force Attack Detection & Investigation

## Overview
This case documents the detection, investigation, and assessment of an SSH brute-force attack targeting a Linux system. The objective was to identify unauthorized access attempts, analyze attacker behavior, assess risk, and determine appropriate escalation actions following SOC best practices.

## Environment
- Operating System: Ubuntu Linux
- Log Source: /var/log/auth.log
- Access Method: SSH
- Tools Used:
  - Linux terminal
  - grep
  - journalctl
  - MITRE ATT&CK framework

## Detection
The incident was detected through repeated authentication failures recorded in the SSH authentication logs.

Command used:
sudo grep "Failed password" /var/log/auth.log

This command revealed multiple failed login attempts originating from the same external IP address within a short time window, indicating a brute-force attack pattern.

## Investigation

### Log Analysis
Key indicators observed:
- High volume of failed SSH login attempts
- Repeated attempts against the same user account
- Source IP address external to the internal network
- Attempts occurring outside normal business hours

Sample indicators:
- Event type: Failed SSH authentication
- Source: External IP address
- Target: Linux SSH service
- Timing: Abnormal (early morning hours)

## Adversary Behavior
The attacker attempted to gain unauthorized access by repeatedly guessing credentials over SSH.

Observed behavior:
- Automated credential guessing
- No evidence of successful authentication
- No privilege escalation observed

This behavior aligns with credential access techniques using brute-force methods.

## MITRE ATT&CK Mapping
- T1110 – Brute Force
  - T1110.001 – Password Guessing

## Severity & Confidence Assessment

Severity: Medium  
- SSH is a critical service
- No successful compromise detected
- Risk of escalation exists if attack succeeds

Confidence: High  
- Clear and repeated log evidence
- Consistent attack pattern
- No ambiguity in indicators

## Response & Escalation
Recommended actions:
- Block the source IP at the firewall level
- Enforce SSH key-based authentication
- Disable password-based SSH authentication
- Continue monitoring for repeated attempts from new IP addresses

Escalation decision:
- Incident documented
- SOC lead notified
- No immediate IR escalation required due to lack of confirmed compromise

## Lessons Learned
- Exposed SSH services are common brute-force targets
- Continuous log monitoring enables early detection
- Automated alerting should be configured in production SOC environments

## Analyst Notes
This investigation demonstrates hands-on experience with:
- Linux authentication log analysis
- Incident triage and investigation
- Severity and confidence classification
- MITRE ATT&CK technique mapping
- SOC-style documentation and decision-making
