<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Digital Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Resources)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Installation Files list</h2>

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

1. **Create a Resource Group**
     - Go to [portal.azure.com](https://portal.azure.com/#home) and sign in with your Azure account.

     - Once logged in, on the left-hand side, click on the "☰", and navigate to "Resource groups" from the Azure services menu.

     - Click on the "+ Create" at the top left of the Resource groups page.

     - We will see a form to create a new resource group. Fill in the following details:
        - *Subscription*: Choose the subscription you want to use; for this guide we will use "Azure Subscription 1".
        - *Resource group*: Give your resource group a name; for this guide we will name it "osTicket".
        - *Region*: Choose the region where you want your resources to be located; for this guide we will use "West US 3".
   
     - Double-check your details, then click on the "Review + create" button at the bottom screen.
   
     - Review the summary, and if everything looks good, click on the "Create" button.
   
     - Azure will now deploy your resource group. This might take a few moments.
   
     - Once deployment is complete, you will receive a notification or see a message confirming that your resource group has been created successfully.

2. **Create a Virtual Machine on Azure:**
   - Navigate the Azure interface and locate the "Virtual Machines" option by pressing the "☰" on the left hand side of the screen.
     
   - Click on the "Create" option prompted in the middle of the screen to create a new virtual machine.

   - Select the first option that says "Azure virtual machine"
   
   - You will see a form to create a virtual machine. Fill in the following details:

     **Project details**
        - *Subscription*: Select the subcription that is already created for us "Azure Subscription 1".
        - *Resource group*: Select our previously created resource group "osTicket".
     
     **Instance details** 
        - *Virtual machine name*: Type whatever name you want in here; for this guide we will call the Virtual Machine "VM1".
        - *Region*: Select the same region from the previously created resource group "West US 3".
        - *Availability options*: Under "Availability options" select "No infrastructure redundancy required"
        - *Image*: Under "image" select "Windows 10 Pro Version 22H2 - x64 Gen2"
        - *Size*: Uder "Size" select atleast 2cpus, 16 GB of memory.

     **Administrator account**
        - *Username*: Create a username; for this guide we will call it "localhost"
        - *Password*: Create a password; for this guide we use "Password12345" as our password.
        - *Confirm password*: Re-enter the password you previously created.

     **Licensing**
        - *License*: Under liscensing press on the check box to confirm lisence hosting rights, and then at the bottom of the screen click on the "Next:" button until you reach the 
               "Networking" tab.
![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/79da3ac4-8d5e-4002-a6ff-94765c2b3117)

     **Networking interface**
       
      - *Virtual network:* A virual network should already be provided for us based off of what we called our virtual machine, it should say "(new) VM1-vnet".
      - *Subnet:* A subnet mask should already be provided for us, it should say "(new) default (10.0.0.0/24)".
      - *Public IP:* A public ip should also be provided for us, it should say "(new) VM1-ip". Once we have confirmed that our public ip is created we will click on "Review + Create", and
          click on the "create" option at the bottom of the screen to create our virtual machine.


4. **Connect to the Virtual Machine:**
   - Once the virtual machine is created go to back to the Azure home page and access the virtual machine by clicking on "VM1" option under our resources.
     ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/e5d4d184-e453-4d30-ada1-a8694b937b9c)

   - After accesing the virtual machine, note down its public IP address.
     ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/356daf23-df81-4f4d-916c-d7e6669bc28c)


   - On your local machine (not on the Azure portal), launch the "Remote Desktop Connection" app. (You can search for it in the Start menu on Windows.)

   - In the Remote Desktop Connection app, enter the public IP address of your Azure virtual machine.

   - Click "Connect" to initiate the connection.

   - If prompted, enter the username and password you set during the virtual machine setup process.

   - Wait for the connection to establish. You should now be connected to your Azure virtual machine remotely.

5. **Enable Windows Features:**

   - Once connected to your virtual machine, go to the Control Panel.

   - Within the Control Panel, locate and open the "Programs" section.

   - Select "Turn Windows features on or off."

   - In the dialog box, navigate to:
     - World Wide Web Services -> Application Development Features

   - Check the boxes for:
     - [X] CGI

     - [X] Common HTTP Features

   - Make sure all Common HTTP Features are checked.

6. **Install and Enable IIS:**
   - After enabling the necessary features, proceed to install and configure Internet Information Services (IIS).

   - In the same "Turn Windows features on or off" dialog box, navigate to:
     - World Wide Web Services

   - Check the box for "Internet Information Services".

   - Click "OK" to install IIS with the selected features.

   *Note: You can verify the installation of IIS by opening a web browser on the virtual machine and navigating to "127.0.0.1". You should see a default web page if IIS is installed and running correctly.* 

7. **Install PHP Manager for IIS and Rewrite Module:**
   - Download PHP Manager for IIS ([PHPManagerForIIS_V1.5.0.msi](https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view)) and the Rewrite Module ([rewrite_amd64_en-US.msi](https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view)) from the [Installation Files](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6).

   - Run the downloaded files and follow the installation wizard to complete the installations.

8. **Create PHP Directory and Install PHP:**
   - Create a folder named "PHP" in the C drive (C:\PHP).
   
   - Download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) from the Installation Files.
   
   - Extract the contents of the downloaded zip file into the C:\PHP directory.

9. **Install VC_redist.x86.exe:**
   - Download VC_redist.x86.exe from the Installation Files.
   
   - Run the downloaded file and follow the setup wizard to complete the installation.

10. **Install MySQL:**
   - Download MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the Installation Files.
   
   - Run the downloaded file and follow the setup wizard:
     - Choose Typical Setup.
     - Launch Configuration Wizard after install.
     - Choose Standard Configuration.
     - Set the root password to "Password1".
     - Execute the process.
!! ATTENTION !! If this appears, choose to “Keep” the file:

11. **Configure IIS:**
   - Search for IIS in the Windows search bar and open it as an administrator.
   
   - Click on PHP Manager and register a new PHP version.
   
   - Provide the path to the php executable file (php-cgi.exe) located in C:\PHP.
   
   - Restart the IIS server.

11. **Install osTicket:**
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
   
12. **Setup osTicket:**
    - Rename "ost-sampleconfig.php" to "ost-config.php" in C:\inetpub\wwwroot\osTicket\include.

    - Set permissions for "ost-config.php" to "Full Control"
