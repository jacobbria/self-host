<div align="center">
  
<img width="800" height=auto alt="download" src="https://github.com/user-attachments/assets/3faa9c1d-0555-4691-9311-82eb95c257f1" />

## Proxmox Credentialed Scanning
> Debian Vulnerability Scan

</div>

### Background 
Proxmox is a type-1 hypervisor based in Debian. Its market share is growing against current hypervisor giant VMWare.

### Objective
* Deploy credentialed vulnerability scan against Proxmox host
* Schedule regular scans against Proxmox host

### Set-up requirements 

Credentialed scans require privledged access. So the following steps were taken
* Create privledged user
* Add specific privledges (used visudo to add new user and give access to specific directories)
* Create private key for use with Nessus

We will be using keys for access to minimize security risk of password. </br>

### Initial Access
First scan was successful.

<div align="center">
  
### Figure 1: Successful Credentialed Scan
<img width="1387" height="195" alt="image" src="https://github.com/user-attachments/assets/15f35240-5aac-43ed-8197-69814770fd8b" />
</div>

### Scheduled Scanning
Easily schedule monthly scans at non-peak hours.
Scan will look at all ports - important to check as IoC can include opening of new ports.

