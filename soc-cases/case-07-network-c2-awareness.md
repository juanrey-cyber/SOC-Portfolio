# SOC Case 07 — Network Indicators & Command-and-Control (C2)

## Overview

This case documents the investigation of suspicious network activity potentially related to Command-and-Control (C2) communication. C2 infrastructure allows attackers to remotely control compromised hosts, issue commands, receive data, and maintain persistence within an environment. Understanding basic network indicators of C2 is essential for SOC Analysts, even without deep packet inspection expertise.

---

## Environment

- Operating Systems: Windows endpoints
- Investigation Context: SOC alert triage and post-compromise analysis
- Log Sources:
  - Firewall logs
  - Proxy logs
  - EDR / SIEM network telemetry (conceptual)
- Network Scope: Internal hosts communicating with external IP addresses

---

## What Is Command-and-Control (Explained Simply)

Command-and-Control (C2) is how attackers communicate with compromised systems.

Once malware is executed, it often:
- Beacons out to an external server
- Receives commands
- Sends stolen data back to the attacker

C2 traffic is often designed to look normal in order to evade detection.

---

## Detection

Suspicious network activity was identified based on abnormal outbound connections from an internal host.

Indicators included:
- Repeated outbound connections to the same external IP or domain
- Network traffic occurring at regular intervals (beaconing)
- Connections outside normal business hours
- Communication over uncommon ports
- Encrypted traffic to unknown destinations

---

## Common C2 Network Indicators

### Beaconing Behavior

Attackers often configure malware to "check in" with the C2 server at regular intervals.

Suspicious patterns:
- Connections every X minutes
- Very small data transfers
- Long-lived but low-volume connections

---

### Suspicious Destinations

Indicators of concern:
- IP addresses with no known business purpose
- Newly registered or low-reputation domains
- Domains generated dynamically (random-looking names)
- Cloud infrastructure abused for malicious hosting

---

### Port and Protocol Abuse

While attackers often use common ports to blend in, unusual usage can still be suspicious.

Examples:
- HTTPS traffic to unknown or untrusted domains
- DNS requests with long or encoded subdomains
- Traffic on non-standard ports without justification

---

## Indicators of Compromise (IOCs)

Potential indicators observed:
- Repeated outbound connections to the same IP
- Beaconing intervals consistent with malware behavior
- Suspicious DNS queries
- Network traffic from a host already involved in prior suspicious activity

---

## MITRE ATT&CK Mapping

The observed behavior maps to the following MITRE ATT&CK techniques:

- T1071 — Application Layer Protocol
- T1071.001 — Web Protocols
- T1071.004 — DNS
- T1041 — Exfiltration Over C2 Channel
- T1105 — Ingress Tool Transfer

---

## Severity and Confidence Assessment

**Severity: High**  
**Confidence: Medium to High**

Rationale:
- Evidence suggests possible C2 communication
- Network patterns align with known attacker behavior
- Lack of confirmed payload limits absolute certainty
- Prior host compromise increases confidence

---

## Response and Next Steps

Recommended SOC actions:
1. Identify and isolate the affected host
2. Block suspicious IPs or domains at network controls
3. Review historical network logs for similar traffic
4. Inspect the endpoint for malware artifacts
5. Escalate to Incident Response if C2 is confirmed
6. Conduct threat hunting for additional affected systems

---

## Analyst Conclusion

The observed network behavior is consistent with potential Command-and-Control activity. While C2 traffic can be intentionally stealthy, the combination of beaconing patterns, suspicious destinations, and prior host compromise elevates the risk. Immediate containment and deeper investigation are required to prevent attacker control and data exfiltration.
