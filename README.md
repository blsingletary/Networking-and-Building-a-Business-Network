<h1>Networking and Building a Business Network</h1>
<h2>Project Overview</h2>

I created this networking home lab in Oracle VirtualBox to develop practical skills commonly required for entry-level IT Support, Helpdesk, and Desktop Support positions.

The lab simulates a small business network using Windows Server 2019 and Windows 10 virtual machines. The Windows Server functions as the network’s domain controller while also providing DNS, DHCP, and file-sharing services. The Windows 10 computers act as employee workstations connected to the business network.

Throughout this project, I will practice assigning IP addresses, creating subnets, configuring DHCP scopes, managing DNS records, joining computers to a domain, testing connectivity, sharing network resources, and troubleshooting common networking problems.

<h2>Lab Objectives</h2>

The main objectives of this project are to:

- Build a small business network in Oracle VirtualBox</br>
- Understand private IP addresses, subnet masks, default gateways, and DNS servers</br>
- Configure static and dynamic IP addressing</br>
- Install and configure DHCP and DNS services</br>
- Create DHCP scopes, exclusions, reservations, and lease settings</br>
- Connect multiple virtual machines to the same virtual network</br>
- Join Windows client computers to an Active Directory domain</br>
- Test network connectivity between servers and client computers</br>
- Use common troubleshooting commands such as ipconfig, ping, tracert, nslookup, arp, and netstat</br>
- Diagnose common DNS, DHCP, addressing, and connectivity problems</br>
- Develop networking experience that can be demonstrated in the workplace</br>
</br>

<h2>Technologies Used:</h2>

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
<img width="1537" height="1059" alt="image" src="https://github.com/user-attachments/assets/b1589fa5-ac24-4d3b-9640-d0c7b390918c" /></br>
</br>
Before Starting up any of the virtual machines I had to configure the network settings in Virtualbox. I left Adapter 1 on Nat so it has connectivity to the internet.
<img width="963" height="464" alt="Screenshot 2026-09-04 204258" src="https://github.com/user-attachments/assets/7bad7c46-ff39-47d3-93b1-44ab33ac0034" /></br>
</br>
Then I enabled Adapter 2 and changed the attachment from Nat to Internal Network and Named it based off of my example organization "Contoso".
<img width="963" height="477" alt="Screenshot 2026-09-04 204305" src="https://github.com/user-attachments/assets/54057e6b-2118-4894-a2c9-f8f9f957d63e" /></br>
</br>
I proceeded to change both user PCs to match the settings of DC01.

<h2>Configure Network Settings</h2>
Next step was to Configure the network settings for DC01
In the Network Connections tab; two ethernet connections are present. The difference between them is that one has an internet connection (NAT) and the other one doesn't (Internal Network)
We have to keep the NAT unchanged so we can remain on the internet. So I'll be configuring the internal network
<img width="789" height="211" alt="image" src="https://github.com/user-attachments/assets/163656f5-f691-40bb-853c-143fa6bbd676" /></br>
</br>
For the network settings I used the following settings:
IP Address: 192.168.10.10
Subnet Mask: 255.255.255.0
DNS: 192.168.10.10 (same as IP)
<img width="390" height="453" alt="image" src="https://github.com/user-attachments/assets/d0c0d72f-17f4-4498-a902-566867c5c0fb" /></br>
</br>
To confirm my settings were saved I used the command "ipconfig /all" in command prompt to see if windows will recognize my changes.
<img width="657" height="272" alt="image" src="https://github.com/user-attachments/assets/69620a1e-4386-47d6-a435-4b12592447b9" /></br>
</br>
I also used the "ping" command to test my connection.
<img width="790" height="745" alt="image" src="https://github.com/user-attachments/assets/915a3835-dd1a-4e91-a6df-6ce058d659fa" /></br>
</br>
<h2>Configure DHCP</h2>
After Installing DHCP using the "add roles and features option", the notification flag has a task telling me to complete the DHCP configuration.
<img width="391" height="252" alt="image" src="https://github.com/user-attachments/assets/fa7334de-09af-443e-b9ff-d2264d4f19b2" /></br>
</br>
I used all the default settings and pressed "commit" which created security groups and Authorized the DHCP server.
<img width="752" height="557" alt="image" src="https://github.com/user-attachments/assets/78067e5b-6f16-4836-973f-9be1590dad47" />
<img width="674" height="494" alt="image" src="https://github.com/user-attachments/assets/831a1595-13fd-40f4-a5a9-22591eb45eb4" /></br>
</br>
Now we have to actaully configure the DHCP and create the scope. </br>
After heading into the DHCP Tool, I selected IPv4 and began creating a scope.
<img width="600" height="526" alt="image" src="https://github.com/user-attachments/assets/0b93891f-4bac-4a35-8b11-f00295ad45e4" />
<img width="510" height="421" alt="image" src="https://github.com/user-attachments/assets/701ad257-879e-4f72-9913-a5a22d795683" /></br>
</br>
For the IP Address Range I used 192.168.10.100 - 192.168.10.200.</br>
Now any workstation that has an IP within this range will be on the same network as me.
<img width="511" height="419" alt="image" src="https://github.com/user-attachments/assets/08a65396-0516-4c1f-8b75-e385bcd887de" /></br>
</br>
I left every option after that at its default value and completed the setup.
<img width="697" height="314" alt="image" src="https://github.com/user-attachments/assets/7bd303ce-ce40-4418-9dba-be4b89a0aad3" /></br>
</br>
<h2>Configuring PC-A01</h2>
Now its time to start configuring our first PC. </br>
I used the same adapter settings as DC01 where adapter 1 is NAT and adapter 2 is the Internal Network
<img width="757" height="437" alt="image" src="https://github.com/user-attachments/assets/8c13c292-bba7-4372-9f77-7c5a41007ac6" /></br>
</br>
This time we won't be changing the IP settings on the PC, since the DHCP will automatically give this PC an IP to use.
<img width="401" height="452" alt="image" src="https://github.com/user-attachments/assets/d19d672b-6ec4-4f60-838f-60e4ab3d6338" /></br>
</br>
To do this I have to open up command prompt and run these three commands
ipconfig /release (releases the IP currently being used)
<img width="611" height="359" alt="image" src="https://github.com/user-attachments/assets/0578d88b-38b4-4282-b0b6-b2d79cc6669b" /></br>
</br>
ipconfig /renew (gives us a new IP based on the DHCP settings)</br>
<img width="607" height="368" alt="image" src="https://github.com/user-attachments/assets/644686f9-f81d-4685-9c1f-d8fc66006dce" /></br>
</br>
ipconfig /all (checks the network information)</br>
<img width="652" height="338" alt="image" src="https://github.com/user-attachments/assets/3b5961b9-8077-4221-bffd-9d6d55bf6a38" /></br>
</br>
Now PC-A01 has successfully been added to the network.
Just for extra measure I used the "ping" command once more
<img width="1079" height="718" alt="image" src="https://github.com/user-attachments/assets/32d255dd-3045-4557-bd8c-deef5ccaa333" /></br>
</br>
Now that everything has been successful, its time to add this PC to the domain.
I used the "sysdm.cpl" command to open up system properties and I made this PC a member of the Domain "contoso.local" which is the name of my example organization.
<img width="974" height="513" alt="image" src="https://github.com/user-attachments/assets/4b9442f0-d2f5-4ca3-8036-4dcf2daa002e" />
<img width="450" height="295" alt="image" src="https://github.com/user-attachments/assets/9c5d8efa-90c6-4527-97e5-855eca850cba" />
<img width="292" height="147" alt="Screenshot 2026-09-07 180615" src="https://github.com/user-attachments/assets/c540c676-715b-4ff6-b7fa-78b60cbd13bf" /></br>
</br>
Now if I go on DC01 and check the active directory, I can find the computer that I just added.
<img width="970" height="638" alt="image" src="https://github.com/user-attachments/assets/a3cec6d7-4d31-4138-86ca-941835573c12" /></br>
</br>
<h2>Configuring PC-B01</h2>
To configure PC-B01 I will use the same process as configuring the first PC.D
Joining the DHCP network
<img width="612" height="298" alt="Screenshot 2026-09-07 183414" src="https://github.com/user-attachments/assets/e83ae19f-dc47-4206-b504-c58147a3e6e4" />
<img width="607" height="381" alt="image" src="https://github.com/user-attachments/assets/0e4e26c8-a681-49ae-86cc-b3446b6dc1e9" /></br>
</br>
Joining the Domain
<img width="975" height="508" alt="image" src="https://github.com/user-attachments/assets/1629138b-ef22-449b-9e06-380be95decea" />
<img width="618" height="489" alt="image" src="https://github.com/user-attachments/assets/5c428e0c-f862-4d0c-9eb6-b87d16f0be7c" /></br>

</br>
<h2>Conclusion</h2>
Completing this networking home lab gave me practical experience building and supporting a small business network in Oracle VirtualBox. I configured Windows Server 2019 as a domain controller, DNS server, DHCP server, and file server. I also connected PC-A01 and PC-B01 to the Contoso domain and verified that they could obtain IP addresses, resolve domain names, communicate with the server, and access network resources.
</br>
</br>
This project strengthened my understanding of IPv4 addressing, subnet masks, DHCP scopes, DNS resolution, virtual network adapters, domain connectivity, and common troubleshooting commands. Working through connectivity and configuration problems also helped me develop a structured troubleshooting process: identify the symptoms, test each network layer, determine the cause, apply a solution, and verify the results.
</br>
</br>
Overall, this lab allowed me to practice responsibilities commonly performed in Helpdesk, IT Support, and Desktop Support roles. It has prepared me to troubleshoot user connectivity problems, manage Windows workstations, support Active Directory environments, and clearly document technical solutions in a professional IT workplace.
