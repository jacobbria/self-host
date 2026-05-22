<div align="center">
<img width="813" height="213" alt="6fa97163639bc3943fbd52295d9d9dac" src="https://github.com/user-attachments/assets/6a6318d1-7252-4f2b-834f-5df8a2959db9" />

## Wazuh
> SIEM & EDR
</div>

### Background

Wazuh is an open-source SIEM and EDR tool. It has extensive community support, replicates many features from 
SIEMs used in enterprise, and has great ease-of-use.

<div align="center">

### Set-up

<img width="1200" height="223" alt="image" src="https://github.com/user-attachments/assets/49581361-bdca-44f9-8d4f-902d5c03bd04" />
</div>

Wazuh has two large components for use - it's manager and it's agents. The manager (what I will refer to as just Wazuh 
or Wazuh Server) is deployed in a Docker instance in an existing node. This is not an ideal choice - placing the server 
in the same path as other Docker instances and VM's means any vulnerability to the baremetal or network itself affects Wazuh and its
ability to collect logs itself. So, when Node X goes dark, no more logging for Node Y or Z. However, you got to war
with the army you have not the army you want. We are working with existing and reclaimed hardware on a local network.

<div align="center">
  
  ### Figure 1: Ideal System Set-up
  <img width="488" height="384" alt="image" src="https://github.com/user-attachments/assets/6a55d5ca-e5ae-47fb-b84a-ffa43fb7e5b9" />

 ### Figure 2: Actual System Set-Up
<img width="467" height="693" alt="image" src="https://github.com/user-attachments/assets/0293e174-c1e9-4044-8168-c6dcaf176094" />


</div>

