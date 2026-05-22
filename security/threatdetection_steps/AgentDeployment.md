<div align="center">
<img width="1211" height="679" alt="1_iRpiffbGnoyJIkdGDTeigQ" src="https://github.com/user-attachments/assets/3f37a7ed-ee65-440f-bb4e-abe33031b06f" />

### Agent Deployment
</div>

---------------

### Goals
- [ ] Windows: Deploy, configure, and ship default, firewall, defender, powershell, and sysmon logs 
- [ ] Linux: Deploy, configure, and ship default, firewall logs
- [ ] macOS:  Deploy, configure, and ship default logs

----------------------


<div align="center">
  
  ### Windows Agent
<img width="1024" height="320" alt="01192022_Blog_Web_Banner_1200_x_320" src="https://github.com/user-attachments/assets/8287907e-c837-4a29-ba02-9a091ed91d8c" />
</div>


The Wazuh agent by default will track log types found in Event Viewer - Application, Security, System.
There are additional logs to be sent back to the Wazuh server. Below are logs and why they are chose.
<div align="center">

  ### Table 1: Additional Logging By Agent
  | Log Type | Reason for Including | Location |
  | --- | --- | --- | 
  | PowerShell | Pevent Living-off-the-Land or fileless execution | Microsoft-Windows-PowerShell/Operational |
  | Sysmon | More in depth monitoring of network activites, account creation, etc | |
  | Defender/Firewall | Will show when defences were activated OR not activated | |
</div>
