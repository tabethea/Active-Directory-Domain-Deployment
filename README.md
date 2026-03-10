# Active Directory Lab

## Description
This repository contains a step by step walkthrough of how i created an Active Directory lab in Oracle VirtualBox. In this lab, I set up a virtual environment using Oracle VirtualBox with Windows 11 and Windows Server 2022 ISOs, creating a Domain Controller with Active Directory, configuring network settings, and establishing a client VM connected to the domain for testing user logins. Running this lab has allowed me to gain hands-on experience with VirtualBox, Active Directory and Windows Networking.

<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b>
- <b>Oracle Virtualbox</b> 

<h2>Environments Used </h2>

- <b>Server 2022</b>
- <b>Windows 11</b>

## Diagram
<img width="1814" height="1079" alt="ad diagram" src="https://github.com/user-attachments/assets/d1487a41-bbf7-49e3-a846-be5652136100" />


# Walkthrough:
## Downloaded Oracle VirtualBox
[Oracle Virtual Box](https://www.virtualbox.org/)

## Downloaded Server 2022 ISO file
[Server 2022](https://info.microsoft.com/ww-landing-windows-server-2022.html)

## Downloaded Windows 11 ISO file
[Windows 11](https://www.microsoft.com/software-download/windows11)

## Configured the first VM
First I configured the VM and named it "Domain Controller." Then I added two network adapters to the Domain Controller.

<b> NAT / External Adapter: Provides internet access from the home network</b>

![image](https://github.com/user-attachments/assets/0df38c4d-fb87-4d01-814d-46a85e914d4a)

<b> Internal Network Adapter: Creates a private LAN for domain-joined hosts</b>

![image](https://github.com/user-attachments/assets/412c3772-9f2f-4a07-96e0-48805811e35f)

## Installed Server 2022
Mounted the Server 2022 ISO and installed it on the VM.

![image](https://github.com/user-attachments/assets/2215ac63-bf24-4d18-9963-9cbe4a8a27fd)
![image](https://github.com/user-attachments/assets/bf120bd4-8d0c-44cb-8b1d-7800494d8231)

## Assigned IP Addressing
Assigned a static IP on the internal network adapter.
The external adapter received an IP automatically from the home router.
The Domain Controller will later serve as the internal LAN’s default gateway.

<img width="1058" height="388" alt="image" src="https://github.com/user-attachments/assets/fb443e62-c5e6-4b04-af74-8c4bc50e1c2a" />

![image](https://github.com/user-attachments/assets/f0779f36-7ba9-43c7-b7e1-e017d1438303)

##  Installed Active Directory Domain Services and created the domain
Installed Active Directory Domain Services and promoted the server to a Domain Controller. Created a new domain.

<img width="722" height="532" alt="image" src="https://github.com/user-attachments/assets/b6dc1912-7ce9-477b-91a9-111c1416bb8e" />

<img width="617" height="457" alt="image" src="https://github.com/user-attachments/assets/3bcab15d-3ae1-4b95-8496-6961b262e632" />



##  Created a dedicated admin account
- Created an OU (Organizational Unit) called ```ADMINS```
- Created a domain administrator account inside it 

<img width="972" height="798" alt="image" src="https://github.com/user-attachments/assets/62c1673e-2d15-41d9-808f-7d8d8a5a0517" />


## Logged in with new domain admin account
Verified the new admin account works by logging in.

![image](https://github.com/user-attachments/assets/5b85320c-e5aa-4c8c-a1f5-e095dc2f6edd)

##  Installed RAS/NAT on the domain controller
Installed Routing and Remote Access Service (RAS) and configured NAT so internal network clients can reach the internet through the Domain Controller.

<img width="745" height="527" alt="image" src="https://github.com/user-attachments/assets/eaacaeb9-e1e0-41fd-8f5a-2b646d252bfd" />
<img width="587" height="413" alt="image" src="https://github.com/user-attachments/assets/11c1051f-7dce-4b4c-b565-f8de749d2fc4" />

##  Configured DHCP on the domain controller
Created a DHCP scope (172.16.0.100–200) to automatically assign internal IPs.
DHCP provides:
- Automatic IP assignment
- Default gateway assignment
- DNS pointing to the DC for authentication

<img width="830" height="522" alt="image" src="https://github.com/user-attachments/assets/7d1601a1-2f14-466b-93e4-2349a8d9d38f" />

##  Used [Power Shell script](https://github.com/joshmadakor1/AD_PS) to create 1000+ users
Ran a PowerShell script to bulk-create users. Large organizations may manage thousands of users. Automation is a real industry requirement.

![image](https://github.com/user-attachments/assets/52c65df7-e83e-43f6-a3ce-4a5c09216765)
![image](https://github.com/user-attachments/assets/5e3bdc48-34a5-4634-8d14-5527a9ea956b)

## Configured Client VM 
Installed Windows 11 on a second VM named Client 1 with only an internal network adapter, so it receives DHCP from the DC.

![image](https://github.com/user-attachments/assets/d0618bf4-6a01-49bc-a97b-2c229916be50)

## Tested DNS and Internet Connectivity
Opened Command Prompt and used ```ping``` to ping ```www.google.com```
Successful ping confirms:
- DHCP assigned an IP
- DNS queries routed through the Domain Controller
- Internet access working via NAT routing

![image](https://github.com/user-attachments/assets/b256ac10-37f9-45f5-b60a-b479be52b834)

## Joined Client 1 to the Domain
Joined the PC to the domain using one of the PowerShell-created accounts.

![image](https://github.com/user-attachments/assets/250eeaeb-234e-4992-9d49-eed10e764308)
![image](https://github.com/user-attachments/assets/d0cd7a6b-50c0-44da-b4f3-6750c5859f1e)

## Restarted and Logged In With Domain User

![image](https://github.com/user-attachments/assets/71eee3e1-e7ce-4024-9fc4-b795b2e3f2a4)
