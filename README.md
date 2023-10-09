<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />






<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain
- Setup Remote Desktop for non-administrative user on Client-1
- Create a bunch of additional users and attempt to log into client with one of the users
- finish

<h2>Setup Resources in Azure </h2>

Create the domain controller VM (Windows Server 2022) named "DC-1.  Take note of the Resource group and virual Network that is created when you create the VM.  Set the VM Domain Controller's NIC private Ip adress to static.  Next create the CLient VM (make sure its Regular Winows 10) Named "CLient-1", use the same resource group and Vnet that was created with DC-1.  Ensure the VM's are in the same Vnet

<p>

![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/e0413973-5bf8-431b-9427-a37d7b0719f7)![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/40e254f6-fee0-459d-b47e-3dfa0afcfeeb)![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/83422a50-98b6-4c52-a69d-a0be900ba712)![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/ef735813-c878-427b-a010-9c562f36c6ad)





</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
