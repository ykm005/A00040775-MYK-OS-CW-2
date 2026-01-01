 Q1) System Architecture Diagram 
 
 <img width="521" height="711" alt="_System Architecture Diagram drawio" src="https://github.com/user-attachments/assets/ad70f9de-f438-4a7f-9b10-8829c0c01666" />


 Q2) I prefer Ubuntu over mint as it is something I have used during my studies for practical work and I feel that it gives me more control over what I download with the command prompts like sudo, apt in the command interface. Linux mint is very similar to Ubuntu, but it depends on what the user needs to use their desktop for and what they’re willing to ignore. 

 Mint is good for beginner Linux users that are used to something like the popular OS Windows, Mint’s Cinnamon and Windows are similar in the interface and resource aspect. 

 With Mint using Cinnamon desktop environment it allows for easy multimedia use and navigation. Ubuntu is good for people who are developers, enterprises and cloud environments. 
 
 It can be resource intensive; this is due to Ubuntu uses GNOME as its default desktop environment. GNOME is a sleek interface. Mint also takes lighter resources in the background. 

 Ubuntu is very good for individuals who want a modern OS with robust development tools, strong community support and integration with cloud services. 
 
 Ubuntu is stronger for developers as it’s community is mostly used by people with that occupation. As someone who does Computer Science, I find Ubuntu to be helpful in my studies.

Q3) I chose to use my Windows 10 host machine as the workstation instead of creating a second Linux VM because it is the most practical and efficient setup for my workflow. Since I already use Windows daily, it makes sense to use it as the main control point for managing my Ubuntu Server. Windows Terminal and PowerShell both support SSH, so I can easily connect to the server without needing another virtual machine running in the background.

Using the host machine also reduces resource usage. Running two VMs at the same time would take more RAM and CPU, which could slow down my system. By keeping the workstation on Windows and only running one VM (Ubuntu Server), I avoid unnecessary performance issues.

Another reason is that this setup reflects real-world practice. In industry, administrators often manage remote Linux servers from their main workstation, not from another VM. Using SSH from Windows gives me a realistic experience of how remote server management works.

Overall, using my Windows 10 host as the workstation is simpler, more efficient, and more aligned with how I already work. It allows me to focus on the server tasks without juggling multiple virtual machines.

Q4) For my network configuration, I chose to use the NAT (Network Address Translation) mode in VirtualBox because it allows my Ubuntu Server to access the internet safely without exposing it directly to my home network. NAT acts as a middle layer between the VM and my WiFi, meaning the server can download updates, install packages, and communicate externally, but devices on my network cannot directly reach the VM. This gives me a secure and controlled environment for my coursework.

Using NAT also keeps the setup simple. VirtualBox automatically assigns the VM an internal IP address in the 10.0.2.x range, and my server received an address such as 10.0.2.15. This address is only accessible inside the virtual environment, which prevents conflicts with my real network while still allowing full internet access for updates and package installations.

Overall, NAT gives me a secure, simple, and realistic network setup. It provides internet access, supports SSH connectivity through port forwarding if needed, and keeps the server isolated from my physical network. This makes it ideal for a headless Ubuntu Server used in a virtualised environment.




Q5) uname prompt

<img width="1280" height="800" alt="1" src="https://github.com/user-attachments/assets/499541bc-10d8-47ba-93d5-a881653377bd" />

free prompt

<img width="1280" height="800" alt="2" src="https://github.com/user-attachments/assets/4ef08f87-e9d4-4f12-9541-fddf2a71a9c6" />

df-h prompt

<img width="1280" height="800" alt="3" src="https://github.com/user-attachments/assets/b73ae03c-6607-4dc6-930c-ce55769c0765" />

ip addr and lsb_release prompt

<img width="1280" height="800" alt="4 and 5" src="https://github.com/user-attachments/assets/439c5e99-ca7d-486c-a72b-9c42771a2a34" />
