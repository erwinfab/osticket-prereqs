<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Internet Information Services (IIS) with CGI enabled
- PHP Manager for IIS (v1.5.0)
- IIS Rewrite Module
- PHP v7.3.8 and Visual C++ Redistributable
- MySQL Server v5.5.62


<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h2>Step 1: VM Setup and File Preparation</h2>
First, provision an Azure Virtual Machine with Windows 10 (e.g., osticket-vm ) and log in via Remote Desktop. Once inside the VM, download and unzip the osTicket-Installation-Files.zip folder to your desktop. This folder contains all the necessary installers and files for the lab.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


<h2>Step 2: Install Web Server & Dependencies</h2>
From the unzipped folder, install all the prerequisites. Start by enabling IIS in Windows, making sure to select CGI under Application Development Features . Next, install PHP Manager for IIS , the Rewrite Module , and the VC redist.x86.exe. Then, create a C:\PHP directory and unzip the php-7.3.8 files into it . Finally, install MySQL 5.5.62 using the Typical Setup, launching the Configuration Wizard to set the root password to "root" .
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<h2>Step 3: Configure IIS and Deploy osTicket</h2>
With the dependencies installed, open IIS Manager as an admin. Go to PHP Manager and register the PHP installation by pointing it to C:\PHP\php-cgi.exe. Reload the IIS server by stopping and starting it. Next, find the osTicket-v1.15.8.zip in your lab files, unzip it, and copy the "upload" folder into c:\inetpub\wwwroot . Rename this "upload" folder to "osTicket" and reload the IIS server again.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<h2>Step 4: Configure PHP Extensions & File Permissions</h2>


In IIS Manager, navigate to the "osTicket" site under "Default" and click "Browse *:80" . You will see some PHP extensions are not enabled. Go back to IIS, double-click PHP Manager on the osTicket site, and click "Enable or disable an extension" . Enable php_imap.dll, php_intl.dll, and php_opcache.dll . Before refreshing the browser, go to C:\inetpub\wwwroot\osTicket\include and rename ost-sampleconfig.php to ost-config.php . You must also change the permissions on this new ost-config.php file: disable inheritance and give the "Everyone" group full control .
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<h2>Step 5: Database Creation and Final Installation</h2>





From the lab files, install HeidiSQL  and open it. Create a new session, connect using the root/root credentials , and create a new database named "osTicket". Now, return to the osTicket setup page in your browser and click "Continue". Fill in the required fields and enter the database details: osTicket (Database Name), root (MySQL Username), and root (MySQL Password) . Click "Install Now!". To complete the setup, perform the post-installation cleanup: delete the C:\inetpub\wwwroot\osTicket\setup folder and change the permissions on ost-config.php to be read-only .
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  











