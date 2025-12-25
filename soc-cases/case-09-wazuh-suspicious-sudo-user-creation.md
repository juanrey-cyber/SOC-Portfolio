# SOC Case 09 — Wazuh: Suspicious sudo usage + new user creation

## Overview
This case simulates a post-compromise scenario: an actor creates a new local user and grants admin privileges using sudo.  
Goal: validate Wazuh alerting, confirm evidence in logs, assess risk, and recommend remediation.

## Environment
- OS: Ubuntu lab
- Telemetry: authentication logs (sudo, user creation, group changes)
- Detection: Wazuh alerts

## Reproduction Steps
1) Create a new user: `sudo useradd -m tempadmin`
2) Set password: `sudo passwd tempadmin`
3) Grant sudo: `sudo usermod -aG sudo tempadmin`
4) Verify: `id tempadmin`, `groups tempadmin`
5) Cleanup: `sudo deluser --remove-home tempadmin`

## Alerts Observed (Wazuh)
- Alert name:
- Rule ID:
- Agent/Host:
- Timestamp:
- Raw log snippet:

## Log Validation
- Source log:
- Evidence observed:

## Assessment
Creating a new privileged local user is high-risk behavior consistent with persistence and privilege escalation.  
In production, this requires immediate investigation to confirm initial access vector and scope.

## MITRE ATT&CK Mapping
- T1136 Create Account
- T1098 Account Manipulation
- T1548 Abuse Elevation Control Mechanism (sudo)

## Severity / Confidence
- Severity:
- Confidence:
- Why:

## Response & Recommendations
- Immediate actions:
- Hardening actions:
- Monitoring actions:

## Lessons Learned (Interview-ready)
-

