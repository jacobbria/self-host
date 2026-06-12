
<div align="center">
  
  <img width="2400" height="700" alt="image" src="https://github.com/user-attachments/assets/00c31442-5ac2-404c-be34-5faea23d974d" />

 ##  Remediation - Benchmark Assessments
</div>

### Goals
- [ ] Perform benchmark assessment on Windows, Mac, and Linux machines using Wazuh Default SCA
- [ ] Perform remediation on systems using security focused reasoning

---------------------

<div align="center">
  
  ### Windows
<img width="1024" height="320" alt="01192022_Blog_Web_Banner_1200_x_320" src="https://github.com/user-attachments/assets/8287907e-c837-4a29-ba02-9a091ed91d8c" />

</div>

### Background
Wazuh has default [Security Configuration Assessments (SCA)](https://documentation.wazuh.com/current/getting-started/use-cases/configuration-assessment.html) which use the Center for Internet Security (CIS) Benchmarks. You can easily find these in the _C:\Program Files (x86)\ossec-agent\ruleset\sca_ file and turn it on in _ossec.conf_. It provides a good starting point to examine security posture of a device. However, it is not an end-all-be-all. It merely provides data in which an analysit takes the full context to see steps should be taken for vulnerability management. 

<div align="center">

### Figure 1: Windows 11 Endpoint SCA Results
<img width="1886" height="595" alt="image" src="https://github.com/user-attachments/assets/e544bab8-8ed1-4f60-ba4d-a96f50ba2d29" />


</div>

### NetBIOS: Remediation
The [Nmap vulnerability scan](security/Vulnerability-Scanning.md) showed a large security flaw common in Windows machines: [NetBIOS](https://en.wikipedia.org/wiki/NetBIOS). A legacy protocol used for [local device communication](https://wirexsystems.com/resource/protocols/netbios/) it is vector for attackers to laterally move.


<div align="center">
  
### Figure 2: Nmap Windows Results 
<img width="792" height="377" alt="image" src="https://github.com/user-attachments/assets/74dd77c9-4872-4d73-8788-96409ca3d046" />
  
### Figure 3: Local Machine NetBIOS Results
<img width="488" height="66" alt="image" src="https://github.com/user-attachments/assets/27b57950-eb99-4be6-87a4-83e8b83b0464" />


</div> 
