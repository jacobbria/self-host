<div align="center">
<img width="1024" height="320" alt="Web_Banner_Windows_Server_2025_-_Blog" src="https://github.com/user-attachments/assets/092f0947-eacd-4356-b687-814329a7315c" />

> Active Directory
</div>

The steps to get a working Active Directory (AD) environment are as follows
- [X] Deploy Windows Server 2022 (Server Core) via Hypervisor (_Hyper V_)
- [X] Install AD DS Services and Configure (_This [guide](https://gal.vin/domain-controller-windows-server-core-walkthrough/) was used_)
- [X] Deploy Windows 11 Admin VM
- [X] Install and configure RSAT Tools 

--------------------


<details>
<summary><strong>Installation</strong></summary


Installation of the Windows Server 2022 and Windows 11 ISO were trivial and comparable to Proxmox and Ubuntu. One interesting hurdle I found was both ISO's would allow me to use my installation media/DVD if Secure Boot was enabled. I was suprised, as Ubuntu simply required changing the Seucre Boot from Windows to Microsoft EUFI Cert. Authority. Even [Microsofts documentation](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/generation-2-virtual-machine-security-features) states it should be compatible.

<div align="Center">

### Figure 1: MS Documentation (Secure Boot)
<img width="531" height="172" alt="image" src="https://github.com/user-attachments/assets/9eafb46a-9d27-4ba7-9bc6-c08a4b45411d" />


</div>

Nonetheless, we were able to boot and install both. </br>

</details>

<details>
<summary><strong>Domain Controller/Server Core</strong></summary
                                                         
The first server will server as the Primary Domain Controller. The following commands were ran and snapshots taken between. </br>

```bash
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools 
Install-ADDSDomainController -DomainName "atreides.local"
```

I ran the following tests to ensure my domain controller properly installed

<div align="Center">

### Figure 2: Post-Install Tests
<img width="1236" height="672" alt="image" src="https://github.com/user-attachments/assets/7c66d0c9-83e9-4a39-a229-07ed48bd4605" />


</div>

It was cool to see the SYSVOL and NETLOGON fileshares. I often interact with troubleshooting client side issues of these. I was familiar with the process of endpoints logging in to check their scripts/GPO but this showed me the internal plumming behind it. 


You can see a jump in system resource usage after the install. No suprise there but it is something I need to keep an eye on and ensure [Zabbix sends alerts](google.com) if resources becomes too in demand for too long.

<div align="Center">
  
### Figure 2: Post Windows Server 2022 (Core) Install Resources
<img width="492" height="162" alt="image" src="https://github.com/user-attachments/assets/410daafd-2eac-425d-83e8-9ead08bc8e1e" />
<img width="545" height="168" alt="image" src="https://github.com/user-attachments/assets/3b9e655d-4c0b-4bb7-8c6b-948ef3010b10" />

</div>

</details>

<details>
<summary><strong>Domain Join</strong></summary
                                       
I tried to run the command [Microsoft recommends in their documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/join-computer-to-domain?tabs=cmd&pivots=windows-server-2025) to join the Windows 11 Pro (called Admin-VM-1) booted up and ran into some issues. It repeated that it couldnt find my domain (_jakebria.com_). I went into the metwork adapter and changed the primary DNS server to be the DC server itself (which mirrors how it should be set up anyways).

<div align="center">
  
### Figure 3: DNS Troubleshooting
<img width="758" height="243" alt="image" src="https://github.com/user-attachments/assets/d4f14bf9-63b7-4679-bb17-752949232cd9" />


</div>

Even with pointing the DNS queries to my DC it still would not find my domain. When specifically querying (see **Figure 3**) it was able to find my domain. The issue (thank you Gemini) appeared to be IPv6. When disabling IPv6 in the network adapter on the endpoint it was able to find, and the join, the domain success (see **Figure 4**). 

<div align="center">

### Figure 4: Domain Join
<img width="636" height="349" alt="image" src="https://github.com/user-attachments/assets/cdf79283-c16a-4fe2-a441-45c11983439d" />
<img width="693" height="107" alt="image" src="https://github.com/user-attachments/assets/4577e327-56f9-4ece-987b-748211aa90f8" />


</div>

</div>
</details>


<details>
<summary><strong>GPO</strong></summary
 </br> </br>
With our functional AD-DS and domain joined devices we can now start to make sure these devices are compliant with business needs. As such, I want to make sure only palace-based employees can access palace devices.
The best way to accomplish this (besides really strong door locks and constant armed guards) is to use GPO to check all users logging in and only allow approved members. To be specific, we want to use **group-based** access control and not user-based access control. So, we will ensure only specific groups and it associated member may login to the computer. 

  </br> </br>

Opening Group Policy editor on a domain-joined device with a domain admin allows us to create, edit, and enforce domains on AD objects. At first I was manually entering which security groups could use the computer. In retrospect, a better method would be to create a Domain Local Security Group - maybe called DL_Palace_Logon - and add Global Groups (Marked by GG_ in the name) in to manage the access. This solution would be  <ul> <li> Easier to manage  <li> Easier to understand <li> Easier to troubleshoot </ul>


<div align="center">

 ### Figure 5: Group Policy
<img width="687" height="277" alt="image" src="https://github.com/user-attachments/assets/ea482d8a-398a-4346-90b7-b8913a758165" />
<img width="631" height="379" alt="image" src="https://github.com/user-attachments/assets/2f52f2ea-83c3-49c7-ad80-8353d8a81398" />
</div>

</br>

I did not make that choice, but even with my existing plan I got it to work. Patreides, member of GG_Atreides_Fam, was able to logon while smaples was not (See **Figure 6**). An example of this being put into place can be found in the proceding subsection below: **Fileshare/Logon**.

<div align="center">

 ### Figure 6: Smaples Login Attempt
<img width="1123" height="766" alt="image" src="https://github.com/user-attachments/assets/4a926b5b-69af-4e78-80ca-4e8dc035be71" />
</div>


<details>
<summary><strong>Fileshare/Logon Script</strong></summary>
Everyone needs to access files - especially files they want to share to others. To accomplish this the Atreides family will have a file share that is exclusive to them.
Using Server Manager I created the file share, hosted on my original DC under its own directory \Shares\Atreides_Share. I have to then decide how to manage both permissions and user access to the file share.

In **GPO** subsection of this page I mentioned a flaw in the style of access control I implemented for access to my workstations. Learning from this, access control will be handed by one Domain Local Security Group - Aptly named DL_AtreideFamilyShare_RW - which will then have users or other groups added. 

 </br> </br>

</details>


</div>
</details>
