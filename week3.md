Q1) Application Selection Matrix  
To evaluate different system performance characteristics, I chose applications that represent specific types of workloads. These tools are commonly used in the industry and provide predictable, controlled workloads that work well for benchmarking.

CPU-Intensive Application  
Application: stress-ng (CPU workers)  
Justification:  
- It is designed specifically for CPU benchmarking.  
- It generates controlled, repeatable CPU loads.  
- It is commonly used for stress testing and performance evaluation.  

RAM-Intensive Application  
Application: stress-ng (memory workers)  
Justification:  
- It includes memory-focused workloads.  
- It allocates and manipulates large blocks of RAM.  
- It is ideal for testing memory pressure and RAM stability.  

I/O-Intensive Application  
Application: fio  
Justification:  
- It is a professional-grade disk benchmarking tool.  
- It simulates realistic read/write patterns.  
- It provides detailed metrics for storage performance (IOPS, throughput, latency).  

Network-Intensive Application  
Application: iperf3  
Justification:  
- It is an industry-standard tool for network performance testing.  
- It measures bandwidth, latency, and throughput.  
- It is useful for evaluating network stability under load.  

Server Application  
Application: Apache2 Web Server  
Justification:  
- It represents a real-world server workload.  
- It allows evaluation of CPU, RAM, and network usage under concurrent connections.  
- It is commonly used in enterprise and web hosting environments.
