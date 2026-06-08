<div align="center">
<img width="1920" height="710" alt="modern-banner-background-full-color-bright-blue-green-gradation-wave-simple-design-wave-style-eps-10-free-vector" src="https://github.com/user-attachments/assets/2748d0b3-469f-4bdb-a69d-bb621dfb0efe" />

  ## Network Discovery
  > Find devices on the network
</div>

--------------------

### Background
Network discovery is a useful tool for both system adminstrators and information security officers. It allows us to see what devices are
connected, if theres any free loaders and/or rogue devices, and get a good network layout. </br> </br>

Two direct scanning tools will be used: Nmap and Nessus. Both tools are great for this task in addtion to having vulnerability scanning.
The network is a small home network which should allow for a stream-lined process of manually checking and comapring the results.
We will also monitor the scan via Wireshark - this provides greater insight into the process and assist with passing the Cysa+ exam. 

### Goals
- [ ] Deploy and run network discovery scan via Nmap
- [ ] Deploy and run network discovery scan via Nessus
- [ ] Compare results (manual and direct)
- [ ] Detect these scan via Wireshark

<div align="center">

## Nmap
<img width="1000" height="333" alt="image" src="https://github.com/user-attachments/assets/ccca0d36-6abe-49a0-b9a0-fa026010b393" />
 
</div>

> Commands used will be explain for authors sake.
### ARP Scan
ARP scanning is a great way to discovery devices on the local network: ARP is require for all devices to communicate (Exlcuding APIPA), it bypassed ICMP/Ping blocks, and ignores firewall issues. 
