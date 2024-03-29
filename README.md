<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket. Into bite size chunks.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Digital Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Resources)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Prerequisites software list</h2>

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Heidi SQL
- rewrite Module
- MySQL
- VC Redist
- osTicket v1.15.8
- Installation Files: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

<h2>Installation Step-by-Step Guide</h2>

1. **Create a Virtual Machine on Azure:**
   - Go to https://portal.azure.com/.
   - Sign in with your Azure account credentials.
   - Navigate to the Azure dashboard and locate the "Virtual Machines" option by pressing the "☰" on the left hand side of the screen.
   - Click on "Add" to create a new virtual machine.
   - Select "Windows 10 Pro" as the operating system.
   - Choose version 22H2.
   - Configure the virtual machine with the following specifications:
     - At least 2 vCPUs.
     - 16 GBs of memory (RAM).
   - Follow the on-screen instructions to complete the virtual machine setup.

2. **Connect to the Virtual Machine:**
   - Once the virtual machine is created, note down its public IP address.
   - On your local machine (not on the Azure portal), launch the "Remote Desktop Connection" app. (You can search for it in the Start menu on Windows.)
   - In the Remote Desktop Connection app, enter the public IP address of your Azure virtual machine.
   - Click "Connect" to initiate the connection.
   - If prompted, enter the username and password you set during the virtual machine setup process.
   - Wait for the connection to establish. You should now be connected to your Azure virtual machine remotely.

3. **Enable Windows Features:**
   - Once connected to your virtual machine, go to the Control Panel.
   - Within the Control Panel, locate and open the "Programs" section.
   - Select "Turn Windows features on or off."
   - In the dialog box, navigate to:
     - World Wide Web Services -> Application Development Features
   - Check the boxes for:
     - [X] CGI

     - [X] Common HTTP Features
   - Make sure all Common HTTP Features are checked.

4. **Install and Enable IIS:**
   - After enabling the necessary features, proceed to install and configure Internet Information Services (IIS).
   - In the same "Turn Windows features on or off" dialog box, navigate to:
     - World Wide Web Services
   - Check the box for "Internet Information Services".
   - Click "OK" to install IIS with the selected features.

   *Note: You can verify the installation of IIS by opening a web browser on the virtual machine and navigating to "127.0.0.1". You should see a default web page if IIS is installed and running correctly.* 

5. **Install PHP Manager for IIS and Rewrite Module:**
   - Download PHP Manager for IIS (<a href="https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view"> PHPManagerForIIS_V1.5.0.msi)) and the Rewrite Module (rewrite_amd64_en-US.msi) from the Installation Files.
   - Run the downloaded files and follow the installation wizard to complete the installations.

6. **Create PHP Directory and Install PHP:**
   - Create a folder named "PHP" in the C drive (C:\PHP).
   - Download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) from the Installation Files.
   - Extract the contents of the downloaded zip file into the C:\PHP directory.

7. **Install VC_redist.x86.exe:**
   - Download VC_redist.x86.exe from the Installation Files.
   - Run the downloaded file and follow the setup wizard to complete the installation.

8. **Install MySQL:**
   - Download MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the Installation Files.
   - Run the downloaded file and follow the setup wizard:
     - Choose Typical Setup.
     - Launch Configuration Wizard after install.
     - Choose Standard Configuration.
     - Set the root password to "Password1".
     - Execute the process.
!! ATTENTION !! If this appears, choose to “Keep” the file:

9. **Configure IIS:**
   - Search for IIS in the Windows search bar and open it as an administrator.
   - Click on PHP Manager and register a new PHP version.
   - Provide the path to the php executable file (php-cgi.exe) located in C:\PHP.
   - Restart the IIS server.

10. **Install osTicket:**
    - Download osTicket v1.15.8 from the Installation Files Folder.
    - Extract and copy the "upload" folder to C:\inetpub\wwwroot.
    - Rename the copied "upload" folder to "osTicket".
    - Reload IIS.
    - On IIS, go to sites -> Default -> osTicket.
    - On the right, click “Browse *:80”.
    - Some extensions might not be enabled on the osTicket browser. To enable them:
       - Go back to IIS, sites -> Default -> osTicket.
       - Double click PHP Manager.
       - Click "Enable or disable an extension" and enable php_imap.dll, php_intl.dll, and php_opcache.dll.
   
11. **Setup osTicket:**
    - Rename "ost-sampleconfig.php" to "ost-config.php" in C:\inetpub\wwwroot\osTicket\include.
    - Set permissions for "ost-config.php" to "Full Control"
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

1.

2.

3.

5.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
