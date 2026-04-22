## IIS, MySQL, and PHP Setup

### 1. Enable IIS and Required Features

The first step in setting up the osTicket environment was enabling Internet Information Services (IIS) on the Windows 11 VM. IIS acts as the web server that hosts the osTicket application and serves it to users through a browser.

In addition to IIS itself, several required features were enabled to support dynamic web applications:

- **CGI** (required for PHP via FastCGI)
- **ISAPI Extensions and Filters**
- **Default Document, Directory Browsing, HTTP Errors, Static Content**
- **IIS Management Console**

These components allow IIS to properly handle web requests and support PHP execution.

📸 Screenshot:  
![IIS Features Enabled](../screenshots/setup/iis-features.png)

---

### 2. Install and Configure MySQL Server

Next, I installed MySQL Server, which serves as the database backend for osTicket. This database is responsible for storing all ticket data, user accounts, and system configurations.

During installation, I configured the server with the following settings:

- **Configuration Type:** Development Computer  
- **Connectivity:** TCP/IP enabled  
- **Port:** 3306  
- **Firewall Access:** Enabled  

This setup allows the osTicket application to communicate with the database locally through standard MySQL networking.

📸 Screenshot:  
![MySQL Type and Networking](../screenshots/setup/mysql-config.png)

---

### 3. Download PHP for Windows

PHP is required for osTicket because it is a PHP-based web application. IIS cannot process PHP files on its own, so PHP must be installed to execute the application logic.

I downloaded PHP from the official website and selected the appropriate Windows version:

- **Version Type:** VS17 x64 Thread Safe  

📸 Screenshot:  
![PHP Download Page](../screenshots/setup/php-download.png)

---

### 4. Configure PHP in IIS (Handler Mapping)

After installing PHP, I configured IIS to pass `.php` files to the PHP engine using FastCGI.

This was done by adding a module mapping in IIS:

- **Request Path:** `*.php`  
- **Module:** FastCgiModule  
- **Executable:** `C:\PHP\php-cgi.exe`  
- **Name:** PHP  

This step is critical because it connects IIS (web server) to PHP (application runtime). Without it, IIS would not be able to execute osTicket’s PHP files.

📸 Screenshot:  
![PHP Handler Mapping](../screenshots/setup/php-handler-mapping.png)

---

### 5. Download osTicket

Once IIS, MySQL, and PHP were configured, I downloaded the osTicket application. osTicket is the actual help desk system that users will interact with.

The downloaded files were later placed into the IIS web root so they could be accessed via the browser.

📸 Screenshot:  
![osTicket Download Page](../screenshots/setup/osticket-download.png)

---

### How These Components Work Together

At this stage, the full application stack is in place:

- **IIS** hosts and serves the web application  
- **PHP** processes application logic and handles requests  
- **MySQL** stores all backend data  
- **osTicket** provides the help desk functionality  

When a user accesses the osTicket site:
1. IIS receives the request  
2. PHP processes the `.php` files  
3. PHP communicates with MySQL  
4. The response is returned to the user  

This forms the foundation required before installing and running osTicket.

## Database Setup and osTicket Installation

### 6. Create the osTicket Database

Before running the osTicket installer, I created a dedicated MySQL database that the application would use to store all ticketing data.

This was done using the following command:

```sql
CREATE DATABASE osticket;

screenshot:

After creting the databse, I verified that it existed by listing all databases:

screenshot

The osticket database appeared in the output, confirming that the backend database was successfully created and ready to be used during installation.

7. Run the osTicket Web Installer

With the database ready, I navigated to the osTicket installer in the browser:

http://localhost/osticket/setup/install.php

During this step, the installer:

Connected to the MySQL database
Created the required tables
Configured system settings
Created the admin account

Once the installation completed successfully, osTicket displayed a confirmation page with links to both the user portal and the staff control panel.

📸 Screenshot:


This marked the point where the application became fully functional.

8. Access the Staff Control Panel

After installation, I accessed the staff control panel using the /scp/ endpoint:

http://localhost/osticket/scp/

This interface is used by administrators and IT staff to manage tickets, users, and system settings.

The following screenshot shows the admin dashboard after successfully logging in. This confirms that the installation was completed correctly and that the system is operational.

📸 Screenshot:

## 9. Configure Desktop Ticket Shortcut via Group Policy

To improve usability in the domain environment, I configured a Group Policy Preference to automatically deploy a desktop shortcut that links directly to the osTicket portal. This allows users to quickly submit IT tickets without needing to manually enter the URL.

The shortcut was created under:


User Configuration → Preferences → Windows Settings → Shortcuts


Initial configuration of the shortcut included:

- **Name:** Submit IT Ticket  
- **Target type:** URL  
- **Location:** Desktop  
- **Target URL:** `http://localhost/osticket`  

📸 Screenshot:  
![GPO Shortcut Initial Config](../screenshots/setup/gpo-shortcut-localhost.png)

After confirming functionality, the target URL was updated to use the server’s IP address so that other devices on the network could access the ticketing system:

- **Updated Target URL:** `http://192.168.4.146/osticket`

📸 Screenshot:  
![GPO Shortcut Updated Config](../screenshots/setup/gpo-shortcut-ip.png)

This ensures that all domain users receive a consistent shortcut pointing to the correct server location.

---

## 10. Expected User-Side Shortcut

After Group Policy is applied, users in the domain will automatically receive the **Submit IT Ticket** shortcut on their desktop.

This shortcut provides direct access to the osTicket submission portal and simulates a real-world enterprise environment where employees can quickly submit support requests.

📸 Screenshot Placeholder:  
![User Desktop Ticket Shortcut](../screenshots/setup/user-ticket-shortcut.png)

---
