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
  <img width="771" height="217" alt="image" src="https://github.com/user-attachments/assets/2124b5bc-e264-4919-b540-40a7dad56a06" />


</div>

In the end the scans were successful.

<div align="center">

  ### Figure 2: Ubuntu Credentialed Scan
  <img width="1390" height="214" alt="image" src="https://github.com/user-attachments/assets/afe6e136-8722-4550-b9cb-13bcacc124cb" />


  ### Figure 3: Ubuntu Uncredentialed Scan
  <img width="1386" height="205" alt="image" src="https://github.com/user-attachments/assets/17d62692-182b-4739-abc3-fc0e325c5b86" />

</div>

### Analysis
The two scan show us that internal and external scans will show different things about the machine and its vulnerabilties. Now, Figure 2 shows the view of an adversary during Reconnaisance as they try and mp the network. Luckily, with the minimal nature of Ubunu LTS, theres not much to to attack at this stage. Remeditation will hopefully be easily perform in another page. </br>
</br>
An interesting thing to compare are the Nessus scans (both internal and external) to Wazuhs SCA benchmark (see Figure 2, Figure 3, and Figure 4). 

<div align="center">

  ### Figure 4: Wazuh Ubuntu 
  <img width="1891" height="364" alt="image" src="https://github.com/user-attachments/assets/025e6ca3-0a8b-481f-8d3d-9ac8ccafe9db" />


</div>

