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
- [x] Deploy and run network discovery scan via Nmap
- [x] Deploy and run network discovery scan via Nessus
- [ ] Compare results (manual and direct)
- [ ] Detect these scan via Wireshark

<div align="center">

## Nmap
<img width="1000" height="333" alt="image" src="https://github.com/user-attachments/assets/ccca0d36-6abe-49a0-b9a0-fa026010b393" />
 
</div>

> Commands used will be explain for authors sake.
### ARP Scan
ARP scanning is a great way to discovery devices on the local network: ARP is require for all devices to communicate (Exlcuding APIPA), it bypassed ICMP/Ping blocks, and ignores firewall issues. </br> </br>

First scan is below... </br>
<div align="center">

### Figure 1: ARP Nmap Scan
```bash
nmap -sn -PR -n <local_ip_range>/24
```
</div>
-sn: Dont use ping (Default) </br>
-PR: Use ARP </br>
-n: Do not use reverse DNS request (Default) </br>

<div align="center">

### Figure 2: ARP Nmap Results
<img width="876" height="796" alt="image" src="https://github.com/user-attachments/assets/5034cea8-de7d-4fbb-8f6d-47ecfcea765a" />

### Figure 3: ARP Zenmap Results
<img width="726" height="613" alt="image" src="https://github.com/user-attachments/assets/4beb1d90-0ba7-4573-8e82-5433349d18e8" />

</div>

### TCP and OS Fingerprint
Lets take a look and see if these devices have open TCP ports open and if we can grab information about the systems
operating systems. </br> </br>

<div align="center">

### Figure 4: Nmap TCP/OS Command
```bash
nmap -sT -n -O <local_ip_range>/24
```

### Figure 5: TCP/OS Nmap Results (Ubuntu)
<img width="946" height="308" alt="image" src="https://github.com/user-attachments/assets/ba365ae1-d10c-49ff-b7a4-fb7e093c82d6" />

</div>
These scans are interesting to look at. You can look the nmap scan here and find out the details about this Ubuntu machine: Notice the MAC address is guessed to be Microft? The Ubuntu machine is a VM on a Hyper-V hypervisor. You can see the several web services open for deployed VM's on the Ubuntu server. It being 1 hop away make sense - its on the local network.


-------------------------------

<div align="center">
  
  ## Nessus
<img width="890" height="276" alt="image" src="https://github.com/user-attachments/assets/02afdb6f-9ae0-43c4-8ad3-a4b49834cd4e" />

</div>

Sad news with Nessus: the free version limits you to 5 unique IP's. So a full network discovery is not possible.
In lieu of the scan below are screenshots of the scans.

<div align="center">

### Figure 6: ARP Nessus Scan
<img width="1128" height="656" alt="image" src="https://github.com/user-attachments/assets/97f074af-cba8-4ec5-8fb1-83716382f2b8" />


</div>



