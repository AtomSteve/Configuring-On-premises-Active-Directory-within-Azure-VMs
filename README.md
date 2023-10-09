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


<h2>Ensure Connectivity between the client and Domain Controller</h2>

</p>
<p>
Login to Client-1 VM with remote desktop and ping the private ip address with ping -t <ip address>.  It shouldnt be able to connect to DC-1 yet.  Login to the DC-1 VM and enable ICMPv4.  Click start -> search Windows Defender Firewall with Advanced Security -> Inbound rules -> Enable both ICMPv4.  Then Check back in with Client-1 and see the changes, its should be pinging the ip address now.  
  
</p>
<br />

![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/c808fde4-922e-4e33-ba03-d3900508e1d5)![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/16f9e8cd-1c4e-44ea-b44c-83424e1c8151)![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/4f1b0bd5-b84a-4f3a-9e53-0fad6e86b907)




<p>

<h2>Install Active Directory</h2>

</p>
<p>
Go ahead and log back into DC-1 if you havn't, go to Server Manager -> Add roles and features -> keep clicking Next until you reach Server Roles and click on Active Directory Domain Services -> hit next and Install.  Next click on the Flag and go to "Promote this Server to a domain controller" -> Add a new forest -> create a root domain name.  Example :mydomain.com -> keep clcking next and Install.  It will sign you out so go ahead and sign back in with the domain.  example: mydomain.com/username
</p>
<br />

![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/a6049555-e279-4174-8947-e3cd9805493e)![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/8c5b5fda-f6e2-4919-bcbe-4332f2b6badc)![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/c5307498-5b5b-40ae-801f-2fc00a7c4a2c)




<p>

<h2>Create an Admin and Normal User Account in AD</h2>

</p>
<p>
To creat an Administrator user clikc on tool -> click on Activ Directory User and Computers -> left click mydomain -> new -> Organizational unit.  name the group _EMPLOYEE's and _Admins or whatever you want to call it.  Now under Admins folder right click and create a user and create a password for them and hit create.  After the user is created right click -> properties -> Member of -> Add to domain admins group.  Now log out of DC-1 and log back in with the user's name and password.  mydomain.com/username :Password.  Now the User credentials will allow you to sighn in to the Domain users account.
  
</p>
<br />

![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/3a4db73f-a878-4ffe-b123-e8f71b7ebfa3)![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/f3e9b60c-8898-49de-9539-bef70fcc0789)![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/ce7db753-163b-4c0e-930e-1248e10e7ca3)

<p>

<h2>Join Client-1 to your domain</h2>

</p>
<p>
From the Azure Portal we need to set Client-1 DNS setting to the Domain Controller's Private ip address.  Go back to the azure portal and get DC-1's private ip address.  Then go to client-1 VM in azure.  CL-1 -> networking -> click on NIC -> DNS Servers -> click on custom and input DC-1's private ip address.  Now in Client-1 VM go to system -> Rename this PC then rename it to the domain name, Example (mydomain.com).  Then it will ask for permisson from the Admin, which is the one that you created.  After Client-1 VM will restart.  Now the user admin that we created will be able to log in to client-1 because it is now in the domain.  


<p>
<br />

![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/d63d2957-8ba1-4ebb-a2a7-bdf4d1abf85e)![image](https://github.com/AtomSteve/Configuring-On-premises-Active-Directory-within-Azure-VMs/assets/147112183/406a86f4-f84f-4967-b9fc-46bfb8f3799d)


