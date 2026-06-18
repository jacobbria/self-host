<div align="center">
<img width="1024" height="320" alt="Web_Banner_Windows_Server_2025_-_Blog" src="https://github.com/user-attachments/assets/092f0947-eacd-4356-b687-814329a7315c" />

> Active Directory
</div>

The steps to get a working Active Directory (AD) environment are as follows
- [X] Deploy Windows Server 2022 (Server Core) via Hypervisor (_Hyper V_)
- [X] Install AD DS Services and Configure (_This [guide](https://gal.vin/domain-controller-windows-server-core-walkthrough/) was used_)
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
The first server will server as the Primary Domain Controller. The follow commands were ran and snapshots taken between. </br>

```bash
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools 
Install-ADDSDomainController -DomainName "jakebria.com"
```

I ran the follow tests to ensure my domain controller properly installed

<div align="Center">

### Figure 2: Post-Install Tests
<img width="1236" height="672" alt="Screenshot 2026-06-15 143524" src="https://github.com/user-attachments/assets/9d799845-ded5-4944-8e3f-ec1a60ddc001" />


</div>

It was cool to see the SYSVOL and NETLOGON fileshares. I often interact with troubleshooting client side issues of these. I was familiar with the process of endpoints logging in to check their scripts/GPO but this showed me the internal plumming behind it. 


You can see a jump in system resource usage after the install. No suprise there but it is something I need to keep an eye on and ensure [Zabbix sends alerts](google.com) if resources becomes too in demand for too long.

<div align="Center">
  
### Figure 2: Post Windows Server 2022 (Core) Install Resources
<img width="492" height="162" alt="image" src="https://github.com/user-attachments/assets/410daafd-2eac-425d-83e8-9ead08bc8e1e" />
<img width="545" height="168" alt="image" src="https://github.com/user-attachments/assets/3b9e655d-4c0b-4bb7-8c6b-948ef3010b10" />

</div>

I tried to run the command [Microsoft recommends in their documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/join-computer-to-domain?tabs=cmd&pivots=windows-server-2025) to join the Windows 11 Pro (called Admin-VM-1) booted up and ran into some issues. It repeated that it couldnt find my domain (_jakebria.com_). I went into the metwork adapter and changed the primary DNS server to be the DC server itself (which mirrors how it should be set up anyways).

<div align="center">
  
### Figure 3: DNS Troubleshooting
<img width="1442" height="347" alt="image" src="https://github.com/user-attachments/assets/3a252092-1085-40d6-b939-0e6dc3efc6bb" />
<img width="992" height="197" alt="image" src="https://github.com/user-attachments/assets/872b2a1f-69c9-4e58-8cdd-d5d1625ea0e0" />

</div>

Even with pointing the DNS queries to my DC it still would not find my domain. When specifically querying (see **Figure 3**) it was able to find my domain. The issue (thank you Gemini) appeared to be IPv6. When disabling IPv6 in the network adapter on the endpoint it was able to find, and the join, the domain success (see **Figure 4**). 

<div align="center">

### Figure 4: Domain Join
<img width="1397" height="597" alt="image" src="https://github.com/user-attachments/assets/a787dc02-ae4b-45c4-b9f8-285f2735a366" />
<img width="656" height="287" alt="image" src="https://github.com/user-attachments/assets/9fa9010c-8511-4a44-b288-25acc67d7aad" />


</div>

### RSAT Tools
Managing the Active Directory and Domain Controller from an endpoint is a common task - we dont need to be remoting into our DC everytime we need to add user. On Admin-1 we will use [this guide](https://windowsforum.com/threads/how-to-install-active-directory-tools-on-windows-11-complete-guide-for-it-pros.361871/) - totally written by AI - to get the tools installed. A little click-ops later using Windows Optional Feature and we added the tools. 


