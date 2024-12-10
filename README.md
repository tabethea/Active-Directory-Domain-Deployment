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
![AD](https://github.com/user-attachments/assets/c1cb1529-ec9c-4e74-b166-b79d1d078a18)

# Walkthrough:
## Downloaded Oracle VirtualBox
[Oracle Virtual Box](https://www.virtualbox.org/)

## Downloaded Server 2022 ISO file
[Server 2022](https://info.microsoft.com/ww-landing-windows-server-2022.html)

## Downloaded Windows 11 ISO file
[Windows 11](https://www.microsoft.com/software-download/windows11)

## Configured the first VM
First I configured the VM and named it "Domain Controller." Then I added two network adapters to the Domain Controller. One for the internet and one for my VirtualBox internal network.

![image](https://github.com/user-attachments/assets/5eb4222d-0802-451b-b2e1-25a94f63e31a)
![image](https://github.com/user-attachments/assets/0df38c4d-fb87-4d01-814d-46a85e914d4a)
![image](https://github.com/user-attachments/assets/412c3772-9f2f-4a07-96e0-48805811e35f)

## Installed Server 2022
Then I powered on the VM, selected the Server 2022 ISO file, then installed it onto the VM.

![image](https://github.com/user-attachments/assets/769aac38-2163-48ca-8ca6-8a77e7020d04)
![image](https://github.com/user-attachments/assets/613e9e7b-8271-4ce6-b65c-614a17957297)
![image](https://github.com/user-attachments/assets/2215ac63-bf24-4d18-9963-9cbe4a8a27fd)
![image](https://github.com/user-attachments/assets/bf120bd4-8d0c-44cb-8b1d-7800494d8231)

## Assigned IP Addressing
Next I assigned IP addressing for the internal network. The external network already has an IP address from my home network, and the domain itself will serve as the default gateway.

![image](https://github.com/user-attachments/assets/20e6e33a-9632-4dc4-9b6a-1759bfb77f92)
![image](https://github.com/user-attachments/assets/f0779f36-7ba9-43c7-b7e1-e017d1438303)

##  Installed Active Directory Domain Services and created the domain
![353981437-caf0e0f5-8759-41e6-82db-3f46d63cbbe6](https://github.com/user-attachments/assets/88b0cfae-1935-4d51-a032-a633d8d7d83c)
![image](https://github.com/user-attachments/assets/117be3de-4cc1-48fd-80c8-fd479305d7eb)
![image](https://github.com/user-attachments/assets/0ba05476-ae22-46f2-ab04-f7c441bbf2ad)
![image](https://github.com/user-attachments/assets/e90375fa-3238-453d-b5ed-ce01f267a166)

##  Created a dedicated admin account
VM restarted so I logged in again, created an organizational unit named "ADMINS," then added my own dedicated admin account. 

![Screenshot 2024-07-31 163542](https://github.com/user-attachments/assets/377ead9b-40f2-48b3-9de3-d21047305efb)
![image](https://github.com/user-attachments/assets/fd80c9af-ade4-423f-a2fe-b09d08ab3cdc)
![image](https://github.com/user-attachments/assets/534eab01-c923-409d-97bd-ad31b77401f9)
![image](https://github.com/user-attachments/assets/176f0df8-ee59-43aa-b4b8-289aa229f11e)
![image](https://github.com/user-attachments/assets/125b4db2-b3fd-463e-a076-dea7c92c0152)
![image](https://github.com/user-attachments/assets/dc2c3ff5-6bc1-4209-9a60-31057093511a)
![image](https://github.com/user-attachments/assets/dabf4774-8cbb-4831-ae8f-53b50501162f)

## Logged in with new domain admin account
![image](https://github.com/user-attachments/assets/5b85320c-e5aa-4c8c-a1f5-e095dc2f6edd)

##  Installed RAS/NAT on the domain controller
This allows Client 1 to acess the internet through the domain controller
![image](https://github.com/user-attachments/assets/c7351538-2582-493c-a0a1-93a8923c5538)
![image](https://github.com/user-attachments/assets/4b840be7-c633-4168-9ac5-9ecfb589c437)
![image](https://github.com/user-attachments/assets/56ae23d3-050f-4736-ab10-2b51d1331249)
![353997931-39ae108b-3f68-4a7c-b950-6f5c747f196b](https://github.com/user-attachments/assets/f2bced77-d14c-4100-8e4c-024b0fdd17e8)
![image](https://github.com/user-attachments/assets/74776873-8f95-4c84-90ec-e1a0d7e4200c)

##  Configured DHCP on the domain controller
Allows for Client 1 to recieve an IP address to browse the internet while in an internal network. Scope ranges from 172.16.0.100-200
![Screenshot 2024-07-31 172154](https://github.com/user-attachments/assets/15c9a998-088e-4c9f-a4c0-82e1f5d80258)
![image](https://github.com/user-attachments/assets/1785852e-d388-4178-8882-154ecdbe3984)
![image](https://github.com/user-attachments/assets/86d34af2-51f7-4462-b841-b6a2921699ec)
![image](https://github.com/user-attachments/assets/534b1388-a49f-42c8-90b2-0940b6d345e2)
![Screenshot 2024-07-31 173104](https://github.com/user-attachments/assets/0a6829eb-f087-424c-b3b6-939922e37c87)

##  Used [Power Shell script](https://github.com/joshmadakor1/AD_PS) to create 1000+ users
Ran Windows Powershell as an administrator and ran script to add 1000+ users

![image](https://github.com/user-attachments/assets/20b3b75e-e63b-47a3-ac22-9edd0fdc67ff)
![image](https://github.com/user-attachments/assets/bea3859a-1946-4888-a5b3-d5d9f1f0a213)
![image](https://github.com/user-attachments/assets/52c65df7-e83e-43f6-a3ce-4a5c09216765)
![image](https://github.com/user-attachments/assets/5e3bdc48-34a5-4634-8d14-5527a9ea956b)

## Configured Client VM 
Created another VM named "Client 1" and installed Windows 11 on it. This will be on the internal network so it can get its addressing from the Domain Controller

![image](https://github.com/user-attachments/assets/edfcd965-1cb0-41c8-8199-398b08a52ca6)
![image](https://github.com/user-attachments/assets/aebd86d7-0c5c-46e8-acd5-2205cc5da114)
![image](https://github.com/user-attachments/assets/1bfd7a70-fe5d-4dff-9a5c-07b4711b3f0b)
![image](https://github.com/user-attachments/assets/d0618bf4-6a01-49bc-a97b-2c229916be50)

## Pinged Website to make sure DNS and infrastructure is working correctly
Used windows command line to ping www.google.com
![image](https://github.com/user-attachments/assets/b256ac10-37f9-45f5-b60a-b479be52b834)

## Added domain to Client 1
Used user credentials from the powershell script to join the domain
![image](https://github.com/user-attachments/assets/250eeaeb-234e-4992-9d49-eed10e764308)
![image](https://github.com/user-attachments/assets/d0cd7a6b-50c0-44da-b4f3-6750c5859f1e)

## Restarted the VM and used user credentials to sign in to the domain from Client 1

![image](https://github.com/user-attachments/assets/71eee3e1-e7ce-4024-9fc4-b795b2e3f2a4)
