<div align="center">
<img width="1081" height="360" alt="Systems Administration Banner" src="https://github.com/user-attachments/assets/a3720a4f-7873-45f2-8c49-bfafe8ffa6d8" />

### Systems Administration Landing
> Deploy, Maintain, Automate
</div>

---

### Goal
Deploy locally available resources on a variety of platforms and operating systems. Monitor these systems, get comfortable troubleshooting, automate deployment with Infrastructure-as-Code (IaC) when possible, and back up systems for Disaster Recovery (DR) and security purposes. Specific objectives for each sub-category are detailed below.

### Automation
- [ ] Maintain optimized baseline templates/images for Linux (Ubuntu) nodes
- [ ] Leverage Terraform and Ansible to provision local VMs and containers dynamically

### Configuration Management
- [ ] Create and maintain a baseline Ansible playbook for standardized Linux node configuration

### High-Availability & Backups
- [ ] Automate local backups adhering to a strict 3-2-1 strategy
- [ ] Create automated alerting thresholds for proactive resource and hardware management

### Monitoring
- [ ] Centralize resource visibility into a single pane of glass
- [ ] Implement Monitoring-as-Code (MaC) via the Zabbix API to ensure consistent, durable, and code-driven monitoring deployments

> ### Security
> Hardening, vulnerability management, and SIEM/SOAR implementations are handled separately in the [Security Repository](https://github.com/jacobbria/self-host/blob/main/security/security-README.md).

### Windows Admin
- [ ] 

-------------------------------
<div align="center">

  ### System Architecture

<img width="1000" height="333" alt="1000_F_520180259_ZMN723ALP7xiWuSYTOTlBKxDnqP4493C" src="https://github.com/user-attachments/assets/698e6382-4296-4ebb-892c-409c41be088b" />

</div>

This system will have 2 nodes of different virtualization technology. Their respective stacks can be seen below (**Figure 1** & **Figure 2**) and will be called **Node 1** and **Node 2**. Node 2 is reclaimed hardware and Node 1 is a dedicated server.

<div align="center">
  
### Figure 1: System Architecture Diagram (Node 1)
<img width="538" height="298" alt="image" src="https://github.com/user-attachments/assets/f4f1670f-07c3-46b8-840e-b27d20f5ccbb" />

### Figure 2: System Architecture Diagram (Node 2)
<img width="420" height="400" alt="image" src="https://github.com/user-attachments/assets/97727f30-4723-452c-898e-9fb76304cc6a" />


</div>


