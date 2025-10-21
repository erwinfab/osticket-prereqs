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
- URL Rewrite Module (v2.1)
- PHP 7.3.8 (Non-Thread Safe)
- Visual C++ Redistributable (VC redist.x86.exe)
- MySQL Server 5.5.62
- HeidiSQL (as a database management tool)

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h2>Step 1: Azure VM Provisioning and Initial File Preparation</h2>
The project began by provisioning a Windows 10 Virtual Machine in Microsoft Azure, named osticket-vm, using labuser as the administrative account. After successfully logging into the VM via Remote Desktop, all necessary installation files, including the osTicket package, PHP, MySQL, and various IIS modules, were downloaded and unzipped onto the desktop, preparing the environment for the core installations.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


<h2>Step 2: IIS and PHP Environment Configuration</h2>
The next phase involved setting up the web server and its scripting engine. Internet Information Services (IIS) was installed from Windows Features, ensuring the Common Gateway Interface (CGI) was also enabled to process PHP scripts. Following this, PHP Manager for IIS and the URL Rewrite Module were installed. PHP version 7.3.8 (Non-Thread Safe) was then unzipped into C:\PHP, the Visual C++ Redistributable was installed, and PHP was registered with IIS Manager, with a subsequent server restart to apply all configurations.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<h2>Step 3: Database Server Installation and Setup</h2>
With the web server configured, the database backend was established. MySQL Server 5.5.62 was installed using the standard configuration, and a root password was set for administrative access. Subsequently, HeidiSQL was installed and used to connect to the newly deployed MySQL server. Within HeidiSQL, a dedicated database named osTicket was created, which would later house all of the help desk application's data.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<h2>Step 4: osTicket Application Deployment and PHP Extension Troubleshooting</h2>


The osTicket application files were deployed by unzipping osTicket-v1.15.8.zip and copying the contents of its upload folder into C:\inetpub\wwwroot, then renaming the folder to osTicket. Upon attempting to access the web installer via http://localhost/osTicket/, it was discovered that critical PHP extensions were missing. This required navigating back to IIS Manager, opening PHP Manager for the osTicket site, and enabling php_imap.dll, php_intl.dll, and php_opcache.dll before proceeding.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<h2>Step 5: osTicket Web Installer Execution and Configuration</h2>





With all prerequisites met, the osTicket web installer was successfully launched. Prior to completing the installation, the ost-sampleconfig.php file within the osTicket\include directory was renamed to ost-config.php, and its file permissions were temporarily elevated to allow the installer to write to it. The helpdesk name, administrator account details, and the previously created database connection settings (Database: osTicket, Username: root, Password: root) were then entered into the installer, culminating in the final "Install Now!" action.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<h2>Step 6: Post-Installation Security and Verification</h2>



To finalize the installation and secure the application, the setup directory located at C:\inetpub\wwwroot\osTicket\setup was promptly deleted. Additionally, the file permissions on C:\inetpub\wwwroot\osTicket\include\ost-config.php were reverted to a more secure "Read-only" state. Finally, successful login to the osTicket staff portal at http://localhost/osTicket/scp/login.php confirmed the complete and secure deployment of the help desk system.
</p>
<br />











