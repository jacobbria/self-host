<div align="center">
  <img width="1500" height="500" alt="1500x500_54_kduPTWJ" src="https://github.com/user-attachments/assets/36f21f33-9c2d-4d59-8d58-897dac7d344f" />

## Ubuntu LTS
> Credentialed Ubuntu Scanning
</div>

### Set-up
Credentialed vulnerability scanning requires privledged access. The follow steps were taken to allow Nessus accesss
* Created new account
* Assigned minimum privledges
* created keys for login
  
### Scanning 
Nessus was able to successfully find and scan the Ubuntu server. </br> </br>
One interesting thing to note was the the amount of resources used in this scan in comparison to scanning of other resources like
the Debian based Proxmox node. This is likely due allowing Nessus to scan the docker instances inside of it - of which there
are many - and because the Debian build is simplier. 

<div align="center">

  ### Figure 1: CPU Resources Used


</div>
