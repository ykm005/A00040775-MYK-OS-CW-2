Q1) Application Selection Matrix  
To evaluate different system performance characteristics, I chose applications that represent specific types of workloads. These tools are commonly used in the industry and provide predictable, controlled workloads that work well for benchmarking.

CPU-Intensive Application  
Application: stress-ng (CPU workers)  
Justification:  
- It is designed specifically for CPU benchmarking.  
- It generates controlled, repeatable CPU loads.  
- It is commonly used for stress testing and performance evaluation.

This is before the stress test has been applied.
<img width="1280" height="800" alt="before stress tests" src="https://github.com/user-attachments/assets/5db5b606-ea47-4cb5-b08f-77c47d6f7668" />

This is how the stress test affected the system. 
Running stress-ng with 4 CPU workers (--cpu 4) caused the system to reach 99.7% CPU usage, as shown in the top output. Each stress-ng-cpu thread used about 23 to 24% of the CPU, fully utilizing all available cores.
<img width="1280" height="800" alt="stress test actual" src="https://github.com/user-attachments/assets/539699bc-8c36-4be0-b0a8-f0a7840ba5c2" />

  

RAM-Intensive Application  
Application: stress-ng (memory workers)  
Justification:  
- It includes memory-focused workloads.  
- It allocates and manipulates large blocks of RAM.  
- It is ideal for testing memory pressure and RAM stability.

<img width="1280" height="800" alt="memory stress test" src="https://github.com/user-attachments/assets/22248bfd-f124-40f9-b19f-b079a8c70d98" />

Running stress-ng with memory workers caused RAM usage to jump to 1.5 GiB out of 1.9 GiB total. This left only 396 MiB free. The system also used 636 MiB for buff/cache, and swap stayed unused. This confirmed that physical memory was enough.

This resulted in:

- Reduced available memory (439 MiB)

- Increased shared memory (439 MiB), indicating active inter-process communication

- No swap usage, showing the system avoided using disk-based memory.

I/O-Intensive Application  
Application: fio  
Justification:  
- It is a professional-grade disk benchmarking tool.  
- It simulates realistic read/write patterns.  
- It provides detailed metrics for storage performance.

<img width="1280" height="800" alt="io" src="https://github.com/user-attachments/assets/4ffb6072-efe3-4745-ac3c-78b9ff46fd08" />


Running fio with a 200 MiB read/write test in /tmp produced:

- Read throughput: 2276 MiB/s

- Write throughput: 2269 MiB/s

- IOPS: ~583k (read), ~581k (write)

- Average read latency: 541 ns

- Average write latency: 813 ns

Network-Intensive Application  
Application: iperf3  
Justification:  
- It is an industry-standard tool for network performance testing.  
- It measures bandwidth, latency, and throughput.  
- It is useful for evaluating network stability under load.
  
<img width="1280" height="800" alt="VirtualBox_ubuntu_01_01_2026_05_20_35" src="https://github.com/user-attachments/assets/26fba719-e9e2-4d4f-beba-76d28576c425" />
<img width="504" height="350" alt="Screenshot 2026-01-01 081721" src="https://github.com/user-attachments/assets/02b6e494-1f12-49a0-9520-743222339142" />

Server Application  
Application: Apache2 Web Server  
Justification:  
- It represents a real-world server workload.  
- It allows evaluation of CPU, RAM, and network usage under concurrent connections.  
- It is commonly used in enterprise and web hosting environments.

<img width="1280" height="800" alt="VirtualBox_ubuntu_01_01_2026_07_34_25" src="https://github.com/user-attachments/assets/f36f4eb0-4fb0-4562-a66f-35a32e1870e3" />


