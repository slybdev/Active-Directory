# Active-Directory

## Objective
The goal of this project was to build a controlled lab environment simulating real-world enterprise systems and security monitoring workflows. I integrated a Windows Active Directory domain, deployed a SIEM (Splunk), and performed attacks using a Kali Linux machine. The objective was to detect and analyze security events like brute-force attacks and simulate adversary techniques using Atomic Red Team.

### Skills Learned
[Bullet Points - Remove this afterwards]

- Building and configuring enterprise-like environments (AD, DNS, static IPs)
- Log ingestion and parsing in Splunk from Windows endpoints
- Configuring Sysmon and Olaf config for detailed event logging
- Performing brute-force attacks and detecting Event ID patterns
- Working with Universal Forwarder and inputs.conf setup
- Hands-on experience with Atomic Red Team attack simulations

### Tools Used
- Splunk (SIEM)
- Splunk Universal Forwarder
- Windows Server 2019 (Domain Controller)
- Windows 10 (Target Endpoint)
- Ubuntu Server (Splunk host)
- Kali Linux (Attacker machine)
- Sysmon + Olaf config (for deep endpoint logging)
- Atomic Red Team (for simulated attacks)
- Crowbar (Cowpatty) (for brute-force attack)

## Steps
*Ref 1: Network Diagram*


![Screenshot 2025-05-08 224237](https://github.com/user-attachments/assets/1e2632f1-7137-46bf-93c8-bf484eac6929)

*2 Configured four VMs:
- Kali Linux (Attacker)
- Ubuntu Server (Splunk SIEM)
- Windows 10 (Target)
- Windows Server 2019 (Domain Controller)
  
![Screenshot 2025-05-09 122323](https://github.com/user-attachments/assets/7e66b573-9efb-48f6-a394-546c04803e95)



*3 Installed and configured Splunk Enterprise on Ubuntu (static IP: 192.168.10.10)


![Screenshot 2025-05-09 123614](https://github.com/user-attachments/assets/08e0567d-655b-415e-b2d3-89a6c057655e)

![Screenshot 2025-05-09 132202](https://github.com/user-attachments/assets/99f0e5d9-7596-4050-839c-2486267ef3f6)


*4 Installed Splunk Universal Forwarder, Sysmon, and Olaf config on both Windows machines
![Screenshot 2025-05-09 234921](https://github.com/user-attachments/assets/dd7674e9-ecc6-4f9a-a6e0-b8acc5a5e1ad)

*5 Edited inputs.conf on both endpoints to forward logs to Splunk



*6 Verified logs were being ingested on Splunk Web via 192.168.10.10:8000
![Screenshot 2025-05-10 002349](https://github.com/user-attachments/assets/a6afd4fd-d343-4ae1-b81a-903289fded72)



*7 Installed AD DS on Windows Server
![Screenshot 2025-05-11 073157](https://github.com/user-attachments/assets/0d739f31-8d80-48f7-b78c-0ae7e94016a5)

*8 Promoted to Domain Controller (domain.local)
![Screenshot 2025-05-11 074955](https://github.com/user-attachments/assets/c1084b19-3aac-4759-bc10-c0fba674fb1e)

*9 Created users: Jane and Bob
![Screenshot 2025-05-11 074818](https://github.com/user-attachments/assets/e468d87f-d859-42c8-a04c-3f2148e8e7e0)
![Screenshot 2025-05-11 074955](https://github.com/user-attachments/assets/ab2a7214-8415-47bf-8faf-817081f719e6)

*10 Configured DNS on Windows 10 to point to the AD server
![Screenshot 2025-05-11 075752](https://github.com/user-attachments/assets/06e4a5ac-dabb-4028-a696-25ce9657f870)

*11 Successfully joined Windows 10 to the domain and logged in as Jane
![Screenshot 2025-05-11 080356](https://github.com/user-attachments/assets/0b6dae9b-9c00-4d88-a2e3-c1e605b043b8)


*12 From Kali, used Crowbar for brute-force attack on Jane’s RDP
![Screenshot 2025-05-11 234431](https://github.com/user-attachments/assets/023b21c4-5740-46f0-8a60-7ccc5de7ba23)

*13 Detected successful brute-force activity in Splunk
![Screenshot 2025-05-12 002927](https://github.com/user-attachments/assets/d1ad8ceb-392a-4a72-b2d3-728a765ce269)

*14 Event ID 4625 (Failed logon)

*15 Event ID 4624 (Successful logon)

*16 Installed Atomic Red Team on AD server

*17 Ran multiple simulations (e.g., credential dumping, UAC bypass)

*18 Verified telemetry was captured in Splunk logs


