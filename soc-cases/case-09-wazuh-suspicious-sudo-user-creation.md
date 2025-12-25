# Case 09 – Ubuntu Privileged Activity & Docker Execution

## Environment
- OS: Ubuntu 24.04.3 LTS
- Hostname: Ubuntu-lab
- User: analyst
- Context: Local lab (VirtualBox)

## Observed Activity
Evidence shows multiple privileged actions performed by user `analyst`:

- sudo sessions opening root shells
- Docker service start
- Docker container execution (alpine)
- cron jobs executed as root

## Evidence Source
- /var/log/auth.log
- Console output (local TTY)

## Key Log Excerpts
(See attached screenshots)

## Analyst Notes
Disk reached 100% utilization due to log growth under /var/ossec,
causing system instability. This reflects a realistic SOC scenario
where improper log retention can lead to operational impact.

