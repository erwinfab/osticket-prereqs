<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>

# osTicket - Prerequisites and Installation
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

## Executive Summary
This project demonstrates the end-to-end installation and configuration of osTicket, an open-source support ticket system. I provisioned a **Windows 10 Virtual Machine** in **Microsoft Azure**, configured **Internet Information Services (IIS) as the web server**, and managed a **MySQL database** to host the platform.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

## Operating Systems Used

- Windows 10</b> (21H2)

## List of Prerequisites

- Internet Information Services (IIS) with CGI enabled
- PHP Manager for IIS (v1.5.0)
- IIS Rewrite Module
- PHP v7.3.8 and Visual C++ Redistributable
- MySQL Server v5.5.62


## Installation Steps


<img width="407" height="303" alt="image" src="https://github.com/user-attachments/assets/51a40b59-af45-47cc-9dd2-f72701f4ad28" /> <img width="727" height="479" alt="image" src="https://github.com/user-attachments/assets/eb6ee987-e9f1-437e-9f37-1b87366f3c60" />


**Step 1**: *VM Provisioning & Environment Setup*
I began by creating an Azure Virtual Machine named "osticket-vm" with the username "labuser". Once the environment was live, I accessed it via Remote Desktop and downloaded the `osTicket-Installation-Files.zip` directly to the desktop.

* To prepare the web environment, I navigated to Windows Features and enabled Internet Information Services (IIS), specifically ensuring the CGI box was checked under Application Development Features.




<img width="369" height="388" alt="image" src="https://github.com/user-attachments/assets/692d9ba3-2e89-4e68-a417-65b9fdc035b9" /> <img width="282" height="241" alt="image" src="https://github.com/user-attachments/assets/fe5910f9-8548-4159-8c2d-d0ab74e13f10" />
<h2></h2>
<img width="507" height="289" alt="image" src="https://github.com/user-attachments/assets/5308f82c-08b6-43d0-8376-8e33c58245ce" />
<h2></h2>
<img width="414" height="197" alt="image" src="https://github.com/user-attachments/assets/2305d4c8-32cf-4c86-b112-bb33d044713b" /> <img width="655" height="392" alt="image" src="https://github.com/user-attachments/assets/85fcfa39-948a-41dc-a584-3fb3bffb7759" />
<h2></h2>
<img width="247" height="170" alt="image" src="https://github.com/user-attachments/assets/330a9145-5d72-4d38-a133-715620e6b24b" /> <img width="308" height="232" alt="image" src="https://github.com/user-attachments/assets/67f6606a-119f-4f9d-921b-84952508a64b" />




</p>


**Step 2**: *Installing Dependencies & Prerequisites*
From the installation folder, I installed several critical backend components:

* **PHP Manager for IIS**: Installed `PHPManagerForIIS_V1.5.0.msi` to manage PHP versions within the web server.

* **URL Rewrite Module**: Installed to handle internal application routing.

* **C++ Redistributable (x86)**: Necessary for PHP to run on the Windows environment.

* I then created a directory at `C:\PH` and unzipped the **PHP 7.3.8** files into it. Within IIS Manager, I registered this PHP installation by pointing it to `C:\PHP\php-cgi.exe` and reloaded the server.



<img width="201" height="113" alt="image" src="https://github.com/user-attachments/assets/a412c86a-c3da-443b-a655-de0e39443eec" /><img width="423" height="561" alt="image" src="https://github.com/user-attachments/assets/2e0e20d2-9b6e-41f4-b331-0f3ab565aaa8" />
<h2></h2>
<img width="167" height="187" alt="image" src="https://github.com/user-attachments/assets/94320087-c1c2-412b-b41a-c969fe8473ee" /> <img width="210" height="140" alt="image" src="https://github.com/user-attachments/assets/f616eb2e-9a44-4fc8-b60f-20c13b156fe4" /> <img width="345" height="351" alt="image" src="https://github.com/user-attachments/assets/c52f0313-6a82-45c2-aac7-9325c3782804" /> <img width="84" height="53" alt="image" src="https://github.com/user-attachments/assets/5e4eac6a-b965-4078-95b1-c89607650664" />




</p>

  
**Step 3**: *MySQL Configuration & osTicket Deployment*
I installed **MySQL 5.5.62** using the **Typical Setup**. During the Configuration Wizard, I chose the **Standard Configuration** and set both the username and password to **"root"**.

Next, I unzipped the osTicket application and moved the **"upload"** folder to `C:\inetpub\wwwroot`, renaming the folder to **"osTicket"**.


<img width="293" height="186" alt="image" src="https://github.com/user-attachments/assets/8101ab98-2fdf-482f-9f23-6b1caa2fd19f" /> <img width="207" height="95" alt="image" src="https://github.com/user-attachments/assets/2d20ea54-ea7a-4d50-ac19-64f21d6b46c9" /> <img width="143" height="227" alt="image" src="https://github.com/user-attachments/assets/47777c10-8a95-464d-9c71-9618d04ca59e" />
<h2></h2>
<img width="402" height="317" alt="image" src="https://github.com/user-attachments/assets/7b18d6b6-14d2-4fc1-8826-2cd5ae1cd6db" /> <img width="99" height="39" alt="image" src="https://github.com/user-attachments/assets/10161dc0-8c9c-44d0-8f29-47add21f9c13" /> <img width="489" height="334" alt="image" src="https://github.com/user-attachments/assets/4989b8e9-d8ee-4ea2-86c7-6ea39ef8c72a" /> <img width="282" height="170" alt="image" src="https://github.com/user-attachments/assets/c158a1d6-45cb-4fce-b961-a70a54d79eca" />






</p>

  
**Step 4**: **PHP Extensions & File Permissions**
* In **IIS Manager**, I navigated to the osTicket site and accessed the **PHP Manager**. I enabled three essential extensions to resolve common installation errors:

* `php_imap.dll` (Required for email fetching)

* `php_intl.dll` (For improved localization)

* `php_opcache.dll` (For faster performance)

I then navigated to `C:\inetpub\wwwroot\osTicket\include` and renamed `ost-sampleconfig.php` to `ost-config.php`. I modified the security settings for this file by **disabling inheritance**, removing all existing permissions, and granting **"Everyone" Full Control**.

<p>
<img width="220" height="148" alt="image" src="https://github.com/user-attachments/assets/7200852b-aa8b-46cf-8ddc-aac906ef8c2c" /> <img width="420" height="286" alt="image" src="https://github.com/user-attachments/assets/8a7b4b54-b83e-41c9-84eb-0bf721e09f56" /> <img width="280" height="149" alt="image" src="https://github.com/user-attachments/assets/c40e3319-c4bb-43d7-ba3f-9c946b61d7df" /> <img width="191" height="95" alt="image" src="https://github.com/user-attachments/assets/e23059f3-6631-4659-8401-e0a8d6721307" /> <img width="274" height="229" alt="image" src="https://github.com/user-attachments/assets/6ecef945-8a04-4e87-9531-5943e3f4acf7" />





</p>
<p>
  
<h2>Step 5: Database Creation and Final Installation</h2>





From the lab files, install HeidiSQL  and open it. Create a new session, connect using the root/root credentials , and create a new database named "osTicket". Now, return to the osTicket setup page in your browser and click "Continue". Fill in the required fields and enter the database details: osTicket (Database Name), root (MySQL Username), and root (MySQL Password) . Click "Install Now!".
</p>
<br />

  

