<div align="center">
<img width="1024" height="320" alt="Web_Banner_Windows_Server_2025_-_Blog" src="https://github.com/user-attachments/assets/092f0947-eacd-4356-b687-814329a7315c" />

> Active Directory
</div>

The steps to get a working Active Directory (AD) environment are as follows
- [X] Deploy Windows Server 2022 (Server Core) via Hypervisor (Hyper V)
- [X] Install AD DS Services and Configure (This [guide](https://gal.vin/domain-controller-windows-server-core-walkthrough/) was used)
- [X] Deploy Windows 11 Admin VM
- [ ] Install and configure RSAT Tools 

--------------------

### Installation

Installation of the Windows Server 2022 and Windows 11 ISO were trivial and comparable to Proxmox and Ubuntu. One interesting hurdle I found was both ISO's would allow me to use my installation media/DVD if Secure Boot was enabled. I was suprised, as Ubuntu simply required changing the Seucre Boot from Windows to Microsoft EUFI Cert. Authority. Even [Microsofts documentation](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/generation-2-virtual-machine-security-features) states it should be compatible.

<div align="Center">

### Figure 1: MS Documentation (Secure Boot)
<img width="531" height="172" alt="image" src="https://github.com/user-attachments/assets/9eafb46a-9d27-4ba7-9bc6-c08a4b45411d" />


</div>

Nonetheless, we were able to boot and install both. </br>

### Server Core
The first server will 


You can see a jump in system resource usage after the install. No suprise there but it is something I need to keep an eye on and ensure [Zabbix sends alerts](google.com) if resources becomes too in demand for too long.

<div align="Center">
  
### Figure 2: Post Windows Server 2022 (Core) Install Resources
<img width="492" height="162" alt="image" src="https://github.com/user-attachments/assets/410daafd-2eac-425d-83e8-9ead08bc8e1e" />
<img width="545" height="168" alt="image" src="https://github.com/user-attachments/assets/3b9e655d-4c0b-4bb7-8c6b-948ef3010b10" />



</div>


