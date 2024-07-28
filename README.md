<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://youtu.be/cG7M3Z-Cek4)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup resources in Azure
- Ensure connectivity between Client-1 and Domain Controller (DC-1)
- Installing Active Directory
- Creating an Admin and Normal User account in AD
- Join Client-1 to your domain
- Setup Remote Desktop (RDP) for non-admin users on Client-1
- Create a bunch of additional users and attempt to log into Client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://github.com/user-attachments/assets/bc4b2f4e-c109-416b-9d04-02c4915d4abc" height="80%" width="80%""/>


</p>
<p>
Diagram
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/b7bb9ba9-4e90-476a-b844-5b07b98397a0" height="80%" width="80%""/>

</p>
<p>
Set up a two VMs, Client-1 Windows VM and DC-1 Windows Server
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/44bd8b6d-455f-4082-9fc2-42b09b31995d" height="80%" width="80%""/>
<img src="https://github.com/user-attachments/assets/530f6a8d-732f-420c-9885-a92bb90b7d41" height="80%" width="80%""/>


</p>
<p>
Changed the ipconfig from dynamic to static meaning my DC-1 ip address will never change.
</p>
<br />

<p>
  <img src="https://github.com/user-attachments/assets/300c80a6-51ce-49fd-8647-be67e765553f" height="80%" width="80%""/>
  <img src="https://github.com/user-attachments/assets/17ccb149-1dc0-4ada-b4b4-a00573ed5ad2" height="80%" width="80%""/>
</p>

<p>
  Using RDP to connect to Client-1 VM. By using command prompt ping -t 10.0.0.4 to ping DC-1 Private IP address and check for connectivity or/and error msgs.
</p>
<br />


<p>
<img src="https://github.com/user-attachments/assets/07a1ce18-286c-49e7-92db-a4ad7c0844ca" height=80%" width="80%""/> 
  <img src="https://github.com/user-attachments/assets/0abf3f4b-8412-4b5c-a531-d671107020df" height=80%" width="80%""/>
  

</p>
 
  
<p>
Login into DC-1 Windows Server by RDP and enabling Windows Defender Firewall w/ Advanced Security to inbound rule on icmpv4, which both of my VMs have so I'm able to
  allow network traffic to enter both of my VMs.
</p>

<br />

<p>
  <img src="https://github.com/user-attachments/assets/a00bd70f-abfd-4694-9c9f-6d1c0ab5bfb3" height="80%" width="80%""/>
  <img src="https://github.com/user-attachments/assets/a5f2f4a0-40ef-4592-a728-c31869e34000" height="80%" width=80%""/>
  
  
</p>
<p>
  Adding roles and features by installing new Active Directory Domain Service and setting up a new forest (domain name) called MYCYBERCAT.COM.
  Able to restart and log back into DC-1 as user mycybercat.com\___
  
</p>
<br />

<p>
  <img src="https://github.com/user-attachments/assets/8778348e-9ef4-47af-b3fb-531d80fde6c6" height="80%" width="80%""/>
  <img src="https://github.com/user-attachments/assets/6da7b926-0155-4592-a1e2-9abb886e6886" height="80%" width="80%""/>


</p>
<p>
  In my Active Directory for Users and Computers, I was able to create two Orgnizational Units (OUs) EMPLOYEES and ADMINS.
</p>
<br />

<p>
  <img src="https://github.com/user-attachments/assets/6dff1d89-d18e-4029-ad3c-6cc3e9b59b2e" height="80%" width="80%""/>
   <img src="https://github.com/user-attachments/assets/f5c60acd-6dba-4871-8170-a55c7bdf4760" height="80%" width="80%""/>
  <img src="https://github.com/user-attachments/assets/af63f3a7-6f44-483e-9095-4bb4b3d74bea" height="80%" width="80%""/>
  
</p>
<p>
  Able to create TWO ADMINS named Julie Doe and Michael Wayne. Logged into Julie Doe's account and able to command prompt to identify whoami.
</p>
<br />

<p>
   <img src="https://github.com/user-attachments/assets/7d083467-94ac-43fc-a17e-540cf5f2f4ad" height="80%" width="80%""/>
    <img src="https://github.com/user-attachments/assets/fc10744c-7b56-4cd7-8084-f1b3f0a10bbb" height="80%" width="80%"/>
   <img src=" https://github.com/user-attachments/assets/7ade219e-3bc9-4da0-81f8-4afbcbf70a96" height="80%" width="80%""/>
  <img src="https://github.com/user-attachments/assets/22f2f023-1186-4e8f-9a8a-15616e66f7d7" height="80%" width="80%""/>
</p>

<p>
  on CL-1, I was unable to use MYCYBERCAT domain due to an error. So I went back into the DNS server and customed my private IP address to be similar to DC-1's private IP address.
</p>
<br/>

<p>
  <img src="https://github.com/user-attachments/assets/bc9542b8-4967-4d6b-a07b-dc09464a4266" height="80%" width="80%""/>
<p>
  <p>
 Now it works! 😊
</p>
<br />

<p>
  <img src="https://github.com/user-attachments/assets/decfc011-2092-4730-bbfd-99ef3195a259" height="80%" width="80%" />
  <img src="https://github.com/user-attachments/assets/f5df04e4-5dbe-4422-8bef-653a9b01fbed" height="80%" width="80%" />

</p>

<p>
  Now able to allow "Domain users" (anyone with MYCYBERCAT domain) to remote desktop.
</p>
<br />

<p>
  <img src="https://github.com/user-attachments/assets/1e05b35b-ac51-4ea0-a0ca-7f3180f34474" height="80%" width="80%" />
</p>
<p>
  Able to create a lot of users by running scripts in PowerShell ISE as an Administrator. 
</p>

<p>
  <img src="https://github.com/user-attachments/assets/7866637b-c5d0-4d05-a75e-ecfcfaa21d31" height="80%" width="80%" />

  <img src="https://github.com/user-attachments/assets/b8aa9c8b-e710-49b8-950f-d28f59f63f89" height="80%" width="80%" />

</p>
<p>
  Now able to log into the employee BOB TUSE account that was created through scripting.
</p>
<br />


