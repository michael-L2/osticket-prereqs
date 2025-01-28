<p align="center">
<img src="https://osticket.com/wp-content/uploads/2021/03/osticket-supsys-new-1-e1616621912452.png" alt="osTicket logo" />
</p>

<h1 align="center">osTicket: Prerequisites and Installation Guide</h1>

This guide details the process of setting up osTicket on a Windows virtual machine (VM). It covers all prerequisites, installation steps, and configuration to help you successfully deploy osTicket in a virtualized environment.

---

## **Environments and Technologies Used**

- **Microsoft Azure** (Virtual Machines/Compute)
- **Remote Desktop Protocol (RDP)**
- **Internet Information Services (IIS)**

---

## **Operating System Used**

- **Windows 10** (21H2)

---

## **Prerequisites**

Before starting, download the following tools:

1. **HeidiSQL v12.3.0**: [Download](https://www.heidisql.com/download.php)
2. **MySQL 5.5.62**: [Download](https://downloads.mysql.com/archives/installer/)
3. **osTicket v1.15.8**: [Download](https://osticket.com/download/)
4. **PHP 7.3.8**: [Download](https://windows.php.net/downloads/releases/)
5. **PHP Manager for IIS v1.5.0**: [Download](https://www.iis.net/downloads/community/2018/05/php-manager-150-for-iis-10)
6. **IIS URL Rewrite Module**: [Download](https://www.iis.net/downloads/microsoft/url-rewrite)
7. **Visual C++ Redistributable (x86)**: [Download](https://aka.ms/vs/17/release/vc_redist.x86.exe)

---

## **Installation Steps**

### **1. Create a Resource Group in Microsoft Azure**
1. In Azure, search for **Resource Group** in the search bar.
2. Select **Create** and name your resource group.
![Resource Group](https://github.com/michael-L2/osticket-prereqs/blob/main/4OsTicket/2rsg.png?raw=true)

---

### **2. Create a Virtual Machine in Azure**
1. Inside the resource group, select **Create** > **Virtual Machine**.
2. Configure your virtual machine with:
   - OS: **Windows 10 Pro**
   - Username: **Create a unique username**
   - Password: **Secure password of your choice**
3. Complete the setup and deploy the virtual machine.
![Virtual Machine](https://github.com/michael-L2/osticket-prereqs/blob/main/4OsTicket/3VMConf.png?raw=true)

---

### **3. Connect to the Virtual Machine**
1. Use **Remote Desktop Protocol (RDP)** to connect to the virtual machine.
2. Enter the public IP address of the VM along with your username and password.
3. Once connected, you’ll have full access to the virtual machine.
![RDP](https://github.com/michael-L2/osticket-prereqs/blob/main/4OsTicket/5RDPWindows.png?raw=true)

---

### **4. Enable IIS on the Virtual Machine**
1. Go to **Control Panel** > **Programs and Features**.
2. Select **Turn Windows Features On or Off**.
3. Enable the following:
   - **Internet Information Services (IIS)**
   - Under **Application Development Features**, enable **CGI**.
4. Click **OK** and allow the installation to complete.
![Enable IIS](https://github.com/michael-L2/osticket-prereqs/blob/main/4OsTicket/10EnablingIIS.png?raw=true)

---

### **5. Transfer Prerequisite Files**
1. Download all required files (from the prerequisites list) on your local computer.
2. Transfer them to the virtual machine via:
   - Drag-and-drop (if using RDP).
   - Uploading them to a cloud storage service (e.g., OneDrive, Google Drive) and downloading on the VM.
![Installers](https://github.com/michael-L2/osticket-prereqs/blob/main/4OsTicket/7OSTReqs.png?raw=true)

---

### **6. Install Prerequisites**
1. **PHP Manager for IIS**: Install and configure PHP with IIS.
2. **URL Rewrite Module**: Install for better URL management in IIS.
3. Extract **PHP 7.3.8** to `C:\PHP`.
4. Install **Visual C++ Redistributable (x86)**.
5. Install **MySQL Server** and set the username/password to `root/root`.

---

### **7. Configure IIS for PHP**
1. Open **IIS Manager**.
2. In PHP Manager, register `php-cgi.exe` from the `C:\PHP` directory.
3. Restart IIS to apply the changes.
![Configure PHP](https://github.com/michael-L2/osticket-prereqs/blob/main/4OsTicket/27StartAndStop.png?raw=true)

---

### **8. Set Up osTicket**
1. Extract the osTicket `.zip` file.
2. Copy the `upload` folder to `C:\inetpub\wwwroot`.
3. Rename the `upload` folder to `osTicket`.
4. Restart IIS and verify setup by navigating to `http://localhost/osTicket` in a web browser.
![osTicket Setup](https://github.com/michael-L2/osticket-prereqs/blob/main/4OsTicket/33OSTConfirmation.png?raw=true)

---

### **9. Enable PHP Extensions**
1. Open **PHP Manager** in IIS.
2. Enable the following extensions:
   - `php_imap.dll`
   - `php_intl.dll`
   - `php_opcache.dll`
3. Restart IIS after enabling the extensions.
![Enable Extensions](https://github.com/michael-L2/osticket-prereqs/blob/main/4OsTicket/35OSTEnable.png?raw=true)

---

### **10. Configure osTicket Settings**
1. Navigate to the `osTicket/include` folder.
2. Rename `ost-sampleconfig.php` to `ost-config.php`.
3. Grant **Full Control** permissions for the file to **Everyone**.
![Configure Permissions](https://github.com/michael-L2/osticket-prereqs/blob/main/4OsTicket/47Done.png?raw=true)

---

### **11. Set Up the osTicket Database**
1. Open **HeidiSQL** and connect to the MySQL server using:
   - Username: `root`
   - Password: `root`
2. Create a new database named `osTicket`.
3. Complete the database setup during the osTicket installation in the browser.
![Database Setup](https://github.com/michael-L2/osticket-prereqs/blob/main/4OsTicket/57OSTFinish.png?raw=true)

---

### **12. Verify Installation**
1. Once the installation is complete, login with the admin credentials you set.
2. Confirm the osTicket dashboard is accessible and functioning.
![Final Confirmation](https://github.com/michael-L2/osticket-prereqs/blob/main/4OsTicket/58ConfirmationOfCompletion.png?raw=true)

---

### **Congratulations!**
Your osTicket system is now successfully installed and ready to use. 🎉
