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

<h2>Setup Virtual Machines</h2>
I began using Oracle Virtualbox and created three Virtual Machines to use. Windows Server 2019 was installed on DC01, while Windows 10 was installed on PC-A01 and PC-B01.
<img width="1537" height="1059" alt="image" src="https://github.com/user-attachments/assets/b1589fa5-ac24-4d3b-9640-d0c7b390918c" />

Before Starting up any of the virtual machines I had to configure the network settings in Virtualbox. I left Adapter 1 on Nat so it has connectivity to the internet.
<img width="963" height="464" alt="Screenshot 2026-09-04 204258" src="https://github.com/user-attachments/assets/7bad7c46-ff39-47d3-93b1-44ab33ac0034" />

Then I enabled Adapter 2 and changed the attachment from Nat to Internal Network and Named it based off of my example organization "Contoso".
<img width="963" height="477" alt="Screenshot 2026-09-04 204305" src="https://github.com/user-attachments/assets/54057e6b-2118-4894-a2c9-f8f9f957d63e" />

I proceeded to change both user PCs to match the settings of DC01.

<h2>Configure Network Settings</h2>
Next step was to Configure the network settings for DC01
In the Network Connections tab; two ethernet connections are present. The difference between them is that one has an internet connection (NAT) and the other one doesn't (Internal Network)
We have to keep the NAT unchanged so we can remain on the internet. So I'll be configuring the internal network
<img width="789" height="211" alt="image" src="https://github.com/user-attachments/assets/163656f5-f691-40bb-853c-143fa6bbd676" />

For the network settings I used the following settings:
IP Address: 192.168.10.10
Subnet Mask: 255.255.255.0
DNS: 192.168.10.10 (same as IP)
<img width="390" height="453" alt="image" src="https://github.com/user-attachments/assets/d0c0d72f-17f4-4498-a902-566867c5c0fb" />

To confirm my settings were saved I used the command "ipconfig /all" in command prompt to see if windows will recognize my changes.
<img width="657" height="272" alt="image" src="https://github.com/user-attachments/assets/69620a1e-4386-47d6-a435-4b12592447b9" />

I also used the "ping" command to test my connection.
<img width="790" height="745" alt="image" src="https://github.com/user-attachments/assets/915a3835-dd1a-4e91-a6df-6ce058d659fa" />

<h2>Configure DHCP</h2>
After Installing DHCP using the "add roles and features option", the notification flag has a task telling me to complete the DHCP configuration.
<img width="391" height="252" alt="image" src="https://github.com/user-attachments/assets/fa7334de-09af-443e-b9ff-d2264d4f19b2" />

I used all the default settings and pressed "commit" which created security groups and Authorized the DHCP server.
<img width="752" height="557" alt="image" src="https://github.com/user-attachments/assets/78067e5b-6f16-4836-973f-9be1590dad47" />
<img width="674" height="494" alt="image" src="https://github.com/user-attachments/assets/831a1595-13fd-40f4-a5a9-22591eb45eb4" />

Now we have to actaully configure the DHCP and create the scope. After heading into the DHCP Tool, I selected IPv4 and began creating a scope.
<img width="600" height="526" alt="image" src="https://github.com/user-attachments/assets/0b93891f-4bac-4a35-8b11-f00295ad45e4" />
<img width="510" height="421" alt="image" src="https://github.com/user-attachments/assets/701ad257-879e-4f72-9913-a5a22d795683" />

For the IP Address Range I used 192.168.10.100 - 192.168.10.200. Now any workstation that has an IP within this range will be on the same network as me.
<img width="511" height="419" alt="image" src="https://github.com/user-attachments/assets/08a65396-0516-4c1f-8b75-e385bcd887de" />

I left every option after that at its default value and completed the setup.
<img width="697" height="314" alt="image" src="https://github.com/user-attachments/assets/7bd303ce-ce40-4418-9dba-be4b89a0aad3" />

