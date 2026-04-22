## IIS, MySQL, and PHP Setup

### 1. Enable IIS and Required Features

The first step in setting up the osTicket environment was enabling Internet Information Services (IIS) on the Windows 11 VM. IIS acts as the web server that hosts the osTicket application and serves it to users through a browser.

In addition to IIS itself, several required features were enabled to support dynamic web applications:

- CGI (used by IIS to enable FastCGI for PHP processing)  
- ISAPI Extensions and Filters  
- Default Document, Directory Browsing, HTTP Errors, Static Content  
- IIS Management Console  

These components allow IIS to properly handle web requests and support PHP execution.

📸 Screenshot:  
![IIS Features Enabled](../screenshots/setup/iis-features.png)

---

### 2. Install and Configure MySQL Server

Next, I installed MySQL Server, which serves as the database backend for osTicket. This database is responsible for storing all ticket data, user accounts, and system configurations.

During installation, I configured the server with the following settings:

- Configuration Type: Development Computer  
- Connectivity: TCP/IP enabled  
- Port: 3306  
- Firewall Access: Enabled  

This setup allows the osTicket application to communicate with the database locally through standard MySQL networking.

📸 Screenshot:  
![MySQL Type and Networking](../screenshots/setup/mysql-config.png)

---

### 3. Download and Configure PHP

PHP is required for osTicket because it is a PHP-based web application. IIS cannot process PHP files on its own, so PHP must be installed to execute the application logic.

I downloaded PHP from the official website and selected the appropriate Windows build for IIS integration.

📸 Screenshot:  
![PHP Download Page](../screenshots/setup/php-download.png)

After installing PHP, I configured the `php.ini` file and enabled required extensions such as:

- mysqli (database connectivity)  
- gd (image processing)  
- mbstring (string handling)  

These extensions are required for osTicket to function properly.

---

### 4. Configure PHP in IIS (Handler Mapping)

After configuring PHP, I connected it to IIS by setting up a handler mapping using FastCGI.

The mapping was configured so that all `.php` files are processed by the PHP engine instead of being treated as static files. This allows IIS to correctly execute the osTicket application.

📸 Screenshot:  
![PHP Handler Mapping](../screenshots/setup/php-handler-mapping.png)

---

### 5. Download and Deploy osTicket

Once IIS, MySQL, and PHP were configured, I downloaded the osTicket application. osTicket is the help desk system that users will interact with.

The application files were placed into the IIS web root directory so they could be accessed through the browser.

📸 Screenshot:  
![osTicket Download Page](../screenshots/setup/osticket-download.png)

---

## Database Setup and osTicket Installation

### 6. Create the osTicket Database

Before running the osTicket installer, I created a dedicated MySQL database that the application would use to store all ticketing data.

I created the database using the MySQL command-line interface and confirmed that the operation completed successfully.

📸 Screenshot:  
![Create osTicket Database](../screenshots/setup/mysql-create-database.png)

After creating the database, I verified that it existed by listing all available databases. The `osticket` database appeared in the output, confirming that it was successfully created and ready to be used during installation.

📸 Screenshot:  
![Verify osTicket Database](../screenshots/setup/mysql-show-databases.png)

---

### 7. Run the osTicket Web Installer

With the database ready, I navigated to the osTicket installer through the browser using the local server path.

During this step, I provided the database name, username, and password to connect osTicket to MySQL. The installer then:

- Established the database connection  
- Created the required tables  
- Configured system settings  
- Created the administrator account  

Once the installation completed successfully, osTicket displayed a confirmation page indicating that the system was ready for use.

📸 Screenshot:  
![osTicket Installation Complete](../screenshots/setup/osticket-install-complete.png)

This marked the point where the application became fully functional.

---

### 8. Access the Staff Control Panel

After installation, I accessed the staff control panel using the `/scp/` endpoint to verify that the system was working correctly.

This interface is used by administrators and IT staff to manage tickets, users, and system settings.

The following screenshot shows the admin dashboard after successfully logging in, confirming that the installation was completed correctly and that the ticketing system is operational.

📸 Screenshot:  
![osTicket Staff Panel](../screenshots/setup/osticket-staff-panel.png)

---

## 9. Configure Desktop Ticket Shortcut via Group Policy

To improve usability in the domain environment, I configured a Group Policy Preference to automatically deploy a desktop shortcut that links directly to the osTicket portal.

The shortcut was created under:

User Configuration → Preferences → Windows Settings → Shortcuts

The initial configuration of the shortcut included:

- Name: Submit IT Ticket  
- Target type: URL  
- Location: Desktop  
- Target URL: http://localhost/osticket  

📸 Screenshot:  
![GPO Shortcut Initial Config](../screenshots/setup/gpo-shortcut-localhost.png)

The localhost URL works only on the server itself, so after confirming that the application was accessible, I updated the shortcut to use the server’s IP address. This allows other devices on the network to access the ticketing system.

- Updated Target URL: http://192.168.4.146/osticket

📸 Screenshot:  
![GPO Shortcut Updated Config](../screenshots/setup/gpo-shortcut-ip.png)

This ensures that all domain users receive a working shortcut that points to the correct server location.

---

## 10. Expected User-Side Shortcut

After Group Policy is applied, users in the domain automatically receive the Submit IT Ticket shortcut on their desktop.

This shortcut provides direct access to the osTicket submission portal and simulates a real-world enterprise environment where employees can quickly submit IT requests.

📸 Screenshot Placeholder:  
![User Desktop Ticket Shortcut](../screenshots/setup/user-ticket-shortcut.png)

---

How the Full System Works

At this point, the full help desk system is operational within the lab environment.

The workflow is as follows:

1. A user clicks the desktop shortcut or navigates to the osTicket page  
2. IIS receives the request and serves the application  
3. PHP executes the osTicket application logic  
4. The application interacts with the MySQL database to store or retrieve ticket data  
5. The response is returned to the user in the browser  

This setup allows the Windows 11 VM to function as a fully operational web application server while also supporting realistic IT support scenarios within the Active Directory lab.
