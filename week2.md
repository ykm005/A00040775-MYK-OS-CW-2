1. Performance Testing Plan  
1.1 Overview  
The performance testing plan aims to set up a repeatable SSH-based monitoring method. This will help me evaluate how the operating system performs under different workloads. The plan includes capturing baseline metrics, applying controlled stress tests, and comparing results before and after security hardening.

Remote monitoring is crucial because the server runs without a graphical interface, so all administration must happen through the command line. This is similar to real-world cloud and DevOps environments where servers are accessed remotely.

1.2 Remote Monitoring Methodology  
All monitoring will occur through secure SSH sessions from the workstation. This guarantees:

No graphical overhead on the server,  
Accurate measurement of system resource usage,  
A realistic simulation of professional remote administration workflows.  

The monitoring process will focus on these areas:

CPU Usage  
I will use tools like top, htop, and vmstat to check CPU load, process behavior, and system responsiveness.

Memory Usage  
Commands such as free -h and vmstat will help find memory pressure, swap usage, and RAM allocation patterns.

Disk I/O  
Using iostat and df -h, I will measure disk read/write rates and pinpoint potential I/O bottlenecks.

Network Activity  
Tools like ss, netstat, iftop, and iperf3 will help analyze active connections, bandwidth use, latency, and throughput.

System Logs  
I will review logs like /var/log/syslog and /var/log/auth.log for any anomalies, authentication attempts, and system warnings.

1.3 Testing Approach  
1. Baseline Capture  
Before applying any security settings, I will record:

CPU load,  
Memory usage,  
Disk activity,  
Network activity,  
Relevant system logs.  

This creates a reference point for later comparison.

2. Stress Testing  
I will evaluate system performance under load using:

stress or stress-ng for CPU, memory, and I/O stress,  
Controlled workloads to imitate real-world usage.  

This helps find bottlenecks and ensures the system stays stable under pressure.

3. Network Load Testing  
Using iperf3, I will measure:

Bandwidth,  
Latency,  
Packet loss,  
Throughput consistency.  

This helps assess how network performance changes after security hardening.

4. Monitoring Under Load  
During stress tests, I will monitor:

CPU saturation,  
Memory exhaustion,  
Disk queue length,  
Network congestion.  

This shows how the OS manages resources and if any processes become unresponsive.

5. Post-Hardening Evaluation  
After implementing security controls in Weeks 4 and 5, I will:

Re-run all baseline and stress tests,  
Compare results against the original baseline,  
Document any performance impact caused by security hardening.  

This ensures the system remains both secure and efficient.

2. Security Configuration Checklist  
This checklist outlines the security controls that will form the baseline configuration for the Linux server. These controls follow standard hardening practices and directly support the assessment requirements.

2.1 SSH Hardening  
Disable root login to prevent direct administrative access.  
Enforce key-based authentication to stop password brute-force attacks.  
Change the default SSH port to reduce automated scanning.  
Restrict SSH access to specific users or groups.  
Disable unused authentication methods and weak encryption.

2.2 Firewall Configuration  
Enable UFW as the host-based firewall.  
Set default policies to deny incoming traffic and allow outgoing traffic.  
Allow only necessary ports (e.g., SSH).  
Enable UFW logging to track dropped packets.  
Apply SSH rate-limiting to reduce brute-force attempts.

2.3 Mandatory Access Control (MAC)  
Ensure AppArmor is installed and running in enforcing mode.  
Verify active profiles using aa-status.  
Apply strict profiles to high-risk services.  
Create or adjust custom profiles as needed.

2.4 Automatic Updates  
Install and set up unattended-upgrades.  
Enable security-only updates.  
Set up automatic reboots for critical kernel patches.  
Review update logs regularly.

2.5 User Privilege Management  
Apply the principle of least privilege to all accounts.  
Grant sudo access only when necessary.  
Audit /etc/passwd and /etc/group for unused accounts.  
Monitor sudo activity via /var/log/auth.log.  
Disable or remove inactive accounts.

2.6 Network Security  
Disable unused network services.  
Regularly check open ports using ss -tulnp.  
Use secure DNS resolvers.  
Monitor network traffic for unusual patterns or spikes.

3. Threat Model  
This threat model identifies three realistic threats to a Linux server and suggests strategies to mitigate each one. It ensures that the security baseline is based on actual risks.

Threat 1: Brute-Force SSH Attacks  
Risk:  
Attackers make repeated login attempts to gain unauthorized access.  

Mitigation:

Enforce key-based authentication,  
Disable root login,  
Change the default SSH port,  
Enable fail2ban,  
Apply SSH rate-limiting via UFW.

Threat 2: Privilege Escalation  
Risk:  
A compromised user account may escalate privileges and gain full system access.  

Mitigation:

Apply least-privilege principles,  
Restrict sudo access,  
Monitor authentication logs,  
Use AppArmor to limit application behavior,  
Keep software updated.

Threat 3: Unpatched Vulnerabilities  
Risk:  
Outdated software may have exploitable security flaws.  

Mitigation:

Enable automatic security updates,  
Review update logs regularly,  
Minimize installed software,  
Reboot after critical updates.

Reflection  
This week improved my understanding of how security planning and performance testing connect in real-world system administration. Designing the testing method early ensures that future configuration changes can be measured objectively, while the security checklist and threat model provide a clear foundation for the hardening work in Weeks 4 and 5.
