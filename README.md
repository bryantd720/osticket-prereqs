<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

**Part 1 (Create Virtual Machine in Azure)**
- Create a Resource Group
- Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
- When creating the VM, allow it to create a new Virtual Network (Vnet)

**Part 2 (Installation)**

- Create an Azure Virtual Machine Windows 10, 4 vCPUs
- Name: vm-osticket
- Username: labuser (or anything you want)
- Password: osTicketPassword1! (example password)
- Login to VM with Remote Desktop Client (use VM's Public IP address creted in Azure portal)
- Open provided link (https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) within VM's internet browser. Every step after this will be executed on the Virtual Machine (Windows). All of the files in the link will be required 

Install / Enable IIS with CGI
- World Wide Web Services -> Application Development Features -> [X] CGI (found in Control Panel/Programs)

Download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

Download and install the Rewrite Module (rewrite_amd64_en-US.msi)

Create the directory C:\PHP

Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP

Download and install VC_redist.x86.exe.

Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) 
- Typical Setup
- Launch Configuration Wizard (after install)
- Standard Configuration
- Use Password1

Open IIS as an administrator

Register PHP from within IIS

Reload IIS (Open IIS, Stop and Start the server)

Install osTicket v1.15.8
- Download osTicket from the Installation Files Folder
- Extract and copy "upload" folder to c:\inetpub\wwwroot
- Within c:\inetpub\wwwroot, rename "upload" folder to "osTicket"

Reload IIS (Open IIS, Stop and Start the server)

- Go to sites -> Default -> osTicket
- On the right, click Browse *:80
- Go back to IIS, sites -> Default -> osTicket
- Double-click PHP Manager
- Click "Enable or disable an extension"
- Enable: php_imap.dll
- Enable: php_intl.dll
- Enable: php_opcache.dll
- Refresh the osTicket site in your browser, observe the changes

Rename: ost-config.php

- From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
- To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

- Assign Permissions: ost-config.php
- Disable inheritance -> Remove All
- New Permissions -> Everyone -> All

- Continue Setting up osTicket in the browser (click Continue)
- Name Helpdesk
- Default email (receives email from customers)

From the Installation Files, download and install HeidiSQL.
- Open Heidi SQL
- Create a new session, root/Password1
- Connect to the session
- Create a database called "osTicket"

Continue Setting up osticket in the browser
- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: Password1
- Click "Install Now!"

Browse to your help desk login page: http://localhost/osTicket/scp/login.php

End Users osTicket URL:
http://localhost/osTicket/ 

(Clean up)
- Delete: C:\inetpub\wwwroot\osTicket\setup
- Set Permissions to "Read" only: C:\inetpub\wwwroot\osTicket\include\ost-config.php

(Notes)
- Browse to your help desk login page: http://localhost/osTicket/scp/login.php  
- End Users osTicket URL: http://localhost/osTicket/ 

<h2>Example Screenshots</h2>

<p>
<img src="https://i.imgur.com/XGj6EhI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is the virtual machine generated in Azure portal.
</p>
<br />


<p>
<img src="https://i.imgur.com/oHQ3HTg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Inside of the Virtual Machine, configuring PHP within Internet Information Services.
</p>
<br />


<p>
<img src="https://i.imgur.com/0M7aaid.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Completing and diplaying IIS setup of the osTicket portal.
</p>
<br />


<p>
<img src="https://i.imgur.com/UhRivlH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Setup remaining admin information and configuring of MySQL settings on portal's installation page.
</p>
<br />
