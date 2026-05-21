<div align="center">
<img width="1024" height="320" alt="Web_Banner_Windows_Server_2025_-_Blog" src="https://github.com/user-attachments/assets/092f0947-eacd-4356-b687-814329a7315c" />

## Windows Scanning
> Windows 11 Vulnerabilities
</div>

### Background
Windows is commonly found in both enterprise and consumer environments. 
However, using Nessus Essentials to do an credential scan of a Windows 11 Home device 
(most common in consumer environments)  can be a bit of a
[headache](https://security.berkeley.edu/faq/nessus-network-vulnerability-scanning/how-do-i-run-credentialed-nessus-scan-windows-computer). </br>
</br>
An agent-based method of scanning would be preferred (similiar to how the Wazuh agent used on this network communicates) but this
feature is not enabled on Nessus Essentials. So, instead an external scan of a Windows 11 machine will be done. 
This gives less details for detecting vulnerabities but does give a different scan perspective which aligns
much more closely with what an external observer on the network would see. 

### Set-up

External agent-less scans are much easier to get set up. 

