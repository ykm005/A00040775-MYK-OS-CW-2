Q1) Performance Testing Plan
SSH‑based monitoring
- Use secure SSH sessions to remotely access system metrics and logs. This allows safe, controlled monitoring without needing physical access to the machine.

Resource usage tools
- Monitor CPU, RAM, disk I/O, and network throughput using tools such as top, htop, vmstat, and iostat.
- I previously used these tools in my Computer Systems module, so I already had a solid understanding of how to interpret system performance and identify abnormal behaviour.

Log analysis
- Review /var/log/syslog, /var/log/auth.log, and service‑specific logs to identify anomalies or security‑related events.
- In my previous Computer Systems coursework (which focused on Windows), I gained experience analysing system and event logs. This helped me understand how operating systems record warnings, authentication attempts, and system activity — knowledge I can apply when planning Linux log analysis.

Network monitoring
- Use ss, netstat, and iftop to observe active connections, open ports, and bandwidth usage. This helps identify unusual traffic or performance bottlenecks.

Baseline comparison
- Capture initial performance metrics and compare them against post‑configuration results to measure the impact of security hardening.

Testing Approach
- Baseline capture
- Record system performance before applying any security configurations to establish a reference point.

Stress testing
- Use tools like stress or stress‑ng to simulate high CPU, memory, and I/O load. This helps evaluate how the system behaves under pressure.

Network load testing
- Use iperf3 to measure network throughput, latency, and stability under controlled load.

Monitoring under load
- Observe system behaviour during stress tests to identify bottlenecks, resource exhaustion, or unexpected slowdowns.

Post‑hardening evaluation
- Re‑run all tests after applying security controls to ensure performance remains acceptable and that hardening has not introduced instability.

Q2) Security Configuration Checklist
This checklist outlines the essential security controls required to establish a secure baseline for a Linux system. Each category includes the key actions that would be implemented as part of a hardening strategy.

SSH Hardening
- Disable root login to prevent direct administrative access.

- Enforce key‑based authentication instead of passwords.

- Change the default SSH port to reduce automated scanning.

- Limit SSH access to specific users or groups using AllowUsers or AllowGroups.

- Disable unused authentication methods and weak ciphers.

Firewall Configuration
- Enable UFW (Uncomplicated Firewall) as the primary host‑based firewall.

- Set default rules to deny incoming and allow outgoing traffic.

- Allow only required ports (e.g., SSH, HTTP if needed).

- Enable UFW logging to track dropped packets.

- Apply SSH rate‑limiting to reduce brute‑force attempts.

Mandatory Access Control (MAC)
Ensure AppArmor is enabled and running in enforcing mode.

- Verify active profiles using aa-status.

- Apply strict profiles to high‑risk services (e.g., SSH, web services).

- Create or adjust custom profiles where necessary to restrict application behaviour.

Automatic Updates
- Install and configure unattended-upgrades for automated security patching.

- Enable security‑only updates to reduce unnecessary changes.

- Configure automatic reboots for critical kernel updates.

- Regularly review update logs to confirm patches are applied.

User Privilege Management
- Apply the principle of least privilege to all user accounts.

- Add users to the sudo group only when required.

- Regularly audit /etc/passwd and /etc/group for unused or unnecessary accounts.

- Monitor sudo activity through /var/log/auth.log.

- Disable or remove inactive accounts to reduce attack surface.

Network Security
- Disable unused network services to minimise exposure.

- Use ss -tulnp to regularly review open ports.

- Use secure DNS resolvers to reduce DNS‑based attacks.

- Monitor network traffic for unusual patterns or spikes.

Q3) Threat Model
This threat model identifies three realistic security threats relevant to a Linux system and outlines appropriate mitigation strategies for each.

Threat 1, Brute-Force SSH Attacks  
Risk:  
Attackers try multiple login attempts to gain unauthorized access to the system.  

Mitigation Strategies:  
- Enforce key-based authentication to eliminate password guessing.  
- Disable root login to prevent targeting of important accounts.  
- Change the default SSH port to reduce automated scans.  
- Enable fail2ban to block repeated failed attempts.  
- Apply SSH rate-limiting through the firewall.  

Threat 2, Privilege Escalation  
Risk:  
A compromised user account could gain elevated privileges to take full control of the system.  

Mitigation Strategies:  
- Apply least-privilege principles to all accounts.  
- Restrict sudo access to only essential users.  
- Monitor authentication logs for suspicious sudo activity.  
- Use AppArmor to limit what applications can access or modify.  
- Keep software updated to fix privilege-escalation vulnerabilities.  

Threat 3, Unpatched Vulnerabilities  
Risk:  
Outdated software may have security flaws that attackers can exploit.  

Mitigation Strategies:  
- Enable automatic security updates using unattended-upgrades.  
- Regularly review update logs to ensure patches are applied.  
- Minimize installed software to reduce potential vulnerabilities.  
- Reboot after critical updates to ensure patches take effect.  
