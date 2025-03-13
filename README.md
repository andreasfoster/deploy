<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Install Active Directory
  
- Step 2: Create a Domain Admin user within the domain
  
- Step 3: Join Client-1 to your domain (mydomain.com)
  
- Step 4: Setup remote desktop for non-admin users on client-1
  
- Step 5: Create a bunch of additional users and attempt to log into client-1 with one of the users

<h2>Install Active Directory</h2>

<p>
Login in into your DC-1 go to ther server manager, after go to add roles and features at the top and continue on until you get to server roles. Once you're there select (Active Direction Domain Services) and continue on and install. Go back to server manager, click the flag at the top and select promote this server to a domain in blue text. Click add new forest and type in (mydomain.com), Create a password and then install. After its installed resign in with mydomain.com\(yourusername). 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>


