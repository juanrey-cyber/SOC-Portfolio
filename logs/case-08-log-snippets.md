# Case 08 – Log Evidence (SSH Brute Force Simulation)

This file contains selected log excerpts used during the investigation.
Logs were manually reviewed to validate Wazuh alerts and Fail2ban behavior.

---

## SSH Authentication Failures (auth.log)

Observed repeated failed login attempts against non-existent users.

Indicators:
- Multiple failed attempts in short time window
- Invalid usernames
- No successful authentication

Conclusion:
Pattern consistent with brute-force or credential guessing activity.

---

## Fail2ban Processing (fail2ban.log)

Fail2ban correctly:
- Parsed SSH authentication failures
- Applied jail `sshd`
- Ignored localhost traffic (`127.0.0.1`) as expected
- Did not trigger bans due to ignore rules

Conclusion:
Fail2ban functioning as designed in a lab environment.
