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

You can see a jump in system resource usage after the install. No suprise there but it is something I need to keep an eye on and ensure [Zabbix sends alerts](google.com) if resources becomes too in demand for too long.

<div align="Center">
  
### Figure 1: Post Windows Server 2022 (Core) Install Resources
<img width="492" height="162" alt="image" src="https://github.com/user-attachments/assets/410daafd-2eac-425d-83e8-9ead08bc8e1e" />
<img width="545" height="168" alt="image" src="https://github.com/user-attachments/assets/3b9e655d-4c0b-4bb7-8c6b-948ef3010b10" />



</div>


