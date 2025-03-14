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

  ![image alt](https://github.com/andreasfoster/deploy/blob/dfe3e3ea5d4a76f19decf86b25ef9f4c54ee92c0/Screenshot%202025-03-12%2022-52-24.png) 
  ![image alt](https://github.com/andreasfoster/deploy/blob/dfe3e3ea5d4a76f19decf86b25ef9f4c54ee92c0/Screenshot%202025-03-12%2022-52-24.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/dfe3e3ea5d4a76f19decf86b25ef9f4c54ee92c0/Screenshot%202025-03-12%2023-21-20.png)

</p>
<p>

<h2>Create a Domain Admin user within the domain</h2>

<p>
Login in into your DC-1 again but with mydomain.com\(yourusername_). Open Active Directory Users and Computers adnd create 2 organizational units named "_EMPLOYEES" and "_ADMINS". right click the mydomain.com, go to new adn the click organizational unit and make sure to put the underscore before the word. Next were going to create a Bot User in the admins folder so later on to test DC-1. Go to the admins folder right click the folder itsself or the side and select new and then user. After create the person but remember to take down the username most importantly because we will use this later on. To give your bot admin rights go to the admins folder you just created it in and right click. go to properties, member of, add and then type domain admins. It might ask you to sign in after you press ok so sign in using the mydomain.com\(theusernameyoucreditedforthebot) and the password or just the orginal sign in info from azure with mydomain.com\. 
</p>
<br />

<p>

  ![image alt](https://github.com/andreasfoster/deploy/blob/0c2bd5ed800c41610b7725edfdf78276211877ef/Screenshot%202025-03-12%2023-41-11.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/0c2bd5ed800c41610b7725edfdf78276211877ef/Screenshot%202025-03-12%2023-43-55.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/0c2bd5ed800c41610b7725edfdf78276211877ef/Screenshot%202025-03-12%2023-45-37.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/0c2bd5ed800c41610b7725edfdf78276211877ef/Screenshot%202025-03-12%2023-46-25.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/0c2bd5ed800c41610b7725edfdf78276211877ef/Screenshot%202025-03-12%2023-48-46.png)
</p>
<p>



<h2>Join Client-1 to your domain (mydomain.com)</h2>

<p>
Log out of DC-1 and resign in with your new bot employee info that you just created and then sign in to client-1 with your original azure username/pw. When youre signed search about computer in the pcs searchbox and click rename this PC (advanced) in the top right corner of the page. select change and switch the member of from workgroup to domain and then type in mydomain.com and then sign in with (mydomain.com\(bot username u created)/pw. Now go back to DC-1s active directory users and computers, explan mydomain.com and verify if client-1 is in the computers folder. Create a new organizational unit called (_CLIENTS) and drag the client-1 from computers folder into it.
</p>
<br />

<p>

  ![image alt](https://github.com/andreasfoster/deploy/blob/ad11d78701a0cb0d05661abd148efd04be5d6159/Screenshot%202025-03-12%2023-53-28.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/ad11d78701a0cb0d05661abd148efd04be5d6159/Screenshot%202025-03-12%2023-53-53.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/ad11d78701a0cb0d05661abd148efd04be5d6159/Screenshot%202025-03-12%2023-55-16.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/ad11d78701a0cb0d05661abd148efd04be5d6159/Screenshot%202025-03-12%2023-57-32.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/ad11d78701a0cb0d05661abd148efd04be5d6159/Screenshot%202025-03-12%2023-59-59.png)

</p>
<p>


<h2>Setup remote desktop for non-admin users on client-1</h2>

<p>
Log out of DC-1 and resign in with your new bot employee info that you just created and then sign in to client-1 with your original azure username/pw. When youre signed search about computer in the pcs searchbox and click rename this PC (advanced) in the top right corner of the page. select change and switch the member of from workgroup to domain and then type in mydomain.com and then sign in with (mydomain.com\(bot username u created)/pw. Now go back to DC-1s active directory users and computers, explan mydomain.com and verify if client-1 is in the computers folder. Create a new organizational unit called (_CLIENTS) and drag the client-1 from computers folder into it.
</p>
<br />

<p>

  ![image alt](https://github.com/andreasfoster/deploy/blob/ad11d78701a0cb0d05661abd148efd04be5d6159/Screenshot%202025-03-12%2023-53-28.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/ad11d78701a0cb0d05661abd148efd04be5d6159/Screenshot%202025-03-12%2023-53-53.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/ad11d78701a0cb0d05661abd148efd04be5d6159/Screenshot%202025-03-12%2023-55-16.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/ad11d78701a0cb0d05661abd148efd04be5d6159/Screenshot%202025-03-12%2023-57-32.png)
  ![image alt](https://github.com/andreasfoster/deploy/blob/ad11d78701a0cb0d05661abd148efd04be5d6159/Screenshot%202025-03-12%2023-59-59.png)

</p>
<p>
