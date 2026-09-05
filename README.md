<h1>Networking Home Lab</h1>
Project Overview

I created this networking home lab in Oracle VirtualBox to develop practical skills commonly required for entry-level IT Support, Helpdesk, and Desktop Support positions.

The lab simulates a small business network using Windows Server 2019 and Windows 10 virtual machines. The Windows Server functions as the network’s domain controller while also providing DNS, DHCP, and file-sharing services. The Windows 10 computers act as employee workstations connected to the business network.

Throughout this project, I will practice assigning IP addresses, creating subnets, configuring DHCP scopes, managing DNS records, joining computers to a domain, testing connectivity, sharing network resources, and troubleshooting common networking problems. I will also document simulated support tickets to demonstrate how I identify, diagnose, resolve, and communicate technical issues.

Lab Objectives

The main objectives of this project are to:

- Build a small business network in Oracle VirtualBox</br>
- Understand private IP addresses, subnet masks, default gateways, and DNS servers</br>
- Configure static and dynamic IP addressing</br>
- Install and configure DHCP and DNS services</br>
- Create DHCP scopes, exclusions, reservations, and lease settings</br>
- Connect multiple virtual machines to the same virtual network</br>
- Join Windows client computers to an Active Directory domain</br>
- Configure shared folders and network permissions</br>
- Test network connectivity between servers and client computers</br>
- Use common troubleshooting commands such as ipconfig, ping, tracert, nslookup, arp, and netstat</br>
- Diagnose common DNS, DHCP, addressing, and connectivity problems</br>
- Develop networking experience that can be demonstrated during interviews</br>
</br>
Technologies Used:

- Oracle VirtualBox</br>
- Windows Server 2019</br>
- Windows 10 or Windows 11</br>
- Active Directory Domain Services</br>
- Domain Name System</br>
- Dynamic Host Configuration Protocol</br>
- IPv4 addressing and subnetting</br>
- Network Address Translation</br>
- VirtualBox Internal Network</br>
- Server Manager</br>
- Active Directory Users and Computers</br>
- File and Storage Services</br>
- Windows Command Prompt</br>
- Windows PowerShell</br>
- GitHub for project documentation</br>

<h2>Build a small business network in Oracle Virtualbox</h2>
I began using Oracle Virtualbox and created three Virtual Machines to use. Windows Server 2019 was installed on DC01, while Windows 10 was installed on PC-A01 and PC-B01.
<img width="1537" height="1059" alt="image" src="https://github.com/user-attachments/assets/b1589fa5-ac24-4d3b-9640-d0c7b390918c" />

Before Starting up any of the virtual machines I had to configure the network settings in Virtualbox. I left Adapter 1 on Nat so it has connectivity to the internet.
<img width="963" height="464" alt="Screenshot 2026-09-04 204258" src="https://github.com/user-attachments/assets/7bad7c46-ff39-47d3-93b1-44ab33ac0034" />

Then I enabled Adapter 2 and changed the attachment from Nat to Internal Network and Named it based off of my example organization "Contoso".
<img width="963" height="477" alt="Screenshot 2026-09-04 204305" src="https://github.com/user-attachments/assets/54057e6b-2118-4894-a2c9-f8f9f957d63e" />

I proceeded to change both user PCs to match the settings of DC01.

<h2>Configure IP Addresses</h2>
Next step was to 
