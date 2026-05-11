<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>

# osTicket - Prerequisites and Installation
*This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.*

### Executive Summary
This project demonstrates the end-to-end installation and configuration of osTicket, an open-source support ticket system. I provisioned a **Windows 10 Virtual Machine** in **Microsoft Azure**, configured **Internet Information Services (IIS) as the web server**, and managed a **MySQL database** to host the platform.

### Environments and Technologies Used
- **Microsoft Azure** (Virtual Machines/Compute)
- **Remote Desktop**
- **Internet Information Services** (IIS)

### Operating Systems Used
- *Windows 10* (21H2)

### List of Prerequisites
- **Internet Information Services (IIS)** with *CGI enabled*
- **PHP Manager** for **IIS** *(v1.5.0)*
- **IIS Rewrite Module**
- **PHP** *v7.3.8* and **Visual C++ Redistributable**
- **MySQL Server** *v5.5.62*

## Installation Steps

**Step 1**: **VM Provisioning & Environment Setup**
* I began by creating an Azure Virtual Machine named "osticket-vm" with the username "labuser". Once the environment was live, I accessed it via Remote Desktop and downloaded the `osTicket-Installation-Files.zip` directly to the desktop.
* To prepare the web environment, I navigated to Windows Features and enabled Internet Information Services (IIS), specifically ensuring the CGI box was checked under Application Development Features.

<img width="962" height="503" alt="image" src="https://github.com/user-attachments/assets/48d0d7ed-b0df-4857-89df-86764754012f" />

---

**Step 2**: **Installing Dependencies & Prerequisites**

From the installation folder, I installed several critical backend components:

* **PHP Manager for IIS**: Installed `PHPManagerForIIS_V1.5.0.msi` to manage PHP versions within the web server.

* **URL Rewrite Module**: Installed to handle internal application routing.

* **C++ Redistributable (x86)**: Necessary for PHP to run on the Windows environment.

I then created a directory at `C:\PH` and unzipped the **PHP 7.3.8** files into it. Within IIS Manager, I registered this PHP installation by pointing it to `C:\PHP\php-cgi.exe` and reloaded the server.

<img width="970" height="510" alt="image" src="https://github.com/user-attachments/assets/662efbc0-1851-4ec8-b103-dbdcbb4d59f7" />

---


**Step 3**: **MySQL Configuration & osTicket Deployment**

* I installed **MySQL 5.5.62** using the **Typical Setup**. During the Configuration Wizard, I chose the **Standard Configuration** and set both the username and password to **"root"**.

* Next, I unzipped the osTicket application and moved the **"upload"** folder to `C:\inetpub\wwwroot`, renaming the folder to **"osTicket"**.

<img width="1044" height="569" alt="image" src="https://github.com/user-attachments/assets/568b7fd6-fd80-4c71-96c2-1d23713b7b80" />

---

**Step 4**: **PHP Extensions & File Permissions**

In **IIS Manager**, I navigated to the osTicket site and accessed the **PHP Manager**. I enabled three essential extensions to resolve common installation errors:

* `php_imap.dll` (Required for email fetching)

* `php_intl.dll` (For improved localization)

* `php_opcache.dll` (For faster performance)

I then navigated to `C:\inetpub\wwwroot\osTicket\include` and renamed `ost-sampleconfig.php` to `ost-config.php`. I modified the security settings for this file by **disabling inheritance**, removing all existing permissions, and granting **"Everyone" Full Control**.

<img width="991" height="532" alt="image" src="https://github.com/user-attachments/assets/7943da34-1721-4025-8076-ff0aa5f2d6fc" />

---

**Step 5**: **Database Creation & Finalization**

* To provide a storage backend for the tickets, I installed **HeidiSQL** and created a new session using the **root** credentials. I then created a new database simply named **"osTicket"**.

* Finally, I opened the web browser to `localhost/osTicket/setup`. I filled out the **Admin User** and **Helpdesk** information, linked the **osTicket** database, and clicked **Install Now** to complete the project.
  
<img width="751" height="578" alt="image" src="https://github.com/user-attachments/assets/598bbc66-01ef-4052-a829-5ed1c7ff6649" />




