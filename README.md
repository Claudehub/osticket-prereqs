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

- Windows 10</b> (22H2)

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
        - *Subscription*: Select the subcription that is already created, "Azure Subscription 1".
        - *Resource group*: Select the previously created resource group "osTicket".
     
     **Instance details** 
        - *Virtual machine name*: Type whatever name you want in here; for this guide we will call the Virtual Machine "VM1".
        - *Region*: Select the same region from the previously created resource group "West US 3".
        - *Availability options*: Under "Availability options" select "No infrastructure redundancy required"
        - *Image*: Under "image" select "Windows 10 Pro Version 22H2 - x64 Gen2"
        - *Size*: Uder "Size" select atleast 2vcpus, 16 GB of memory.

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


3. **Connect to the Virtual Machine:**
   - Once the virtual machine is complete for deployment go back to the Azure home page by pressing on the blue "Home" button located at the top left of the screen.
   ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/5b4aa4f8-beb0-499d-b1cc-712fa4df4363)

   - Access the virtual machine by clicking on "VM1" option under our resources.
     ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/e5d4d184-e453-4d30-ada1-a8694b937b9c)

    - After accesing the virtual machine, note down its public IP address.
     ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/356daf23-df81-4f4d-916c-d7e6669bc28c)

    - On your local machine (not on the Azure portal), launch the "Remote Desktop Connection" app. (You can search for it in the Start menu on Windows.)

    - In the Remote Desktop Connection app, enter the public IP address of your Azure virtual machine.

    - Click "Connect" to initiate the connection.
  
    - Once the connection is established you will see a tab that prompts you to enter credentials. Press on "More choices"
   
   ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/7975dc97-f3c7-45c8-93b8-bb5274129fb1)

    - Once prompted, click on "Use a different account", and enter the "User name" and "Password" you set during the virtual machine setup process.

   ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/725467f0-4596-4b1e-a0ad-1e22f245becf)

    
    
    
    
    - Upon initiating the connection, a prompt will appear that will ask if you still wish to proceed with the connection, press "Yes".
     
     ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/05ee5183-21c7-4aa3-b210-cbc5a71c2fac)

    - Wait for the connection to establish. You should now be connected to your Azure virtual machine remotely.

4. **Enable Windows Features:**

   - After connecting to your virtual machine, a prompt will appear to adjust privacy settings. Since these settings are not required for this guide, just disable all of them, and then click "Accept".
   
   - After logging into the virtual machine, access the Control Panel by using the search function at the bottom-left corner of the screen.
   
   ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/0182f3bc-a0dc-435b-a3bd-3fbeb3a2396d)
    
   - Within the Control Panel, you will see multiple adjustable computer settings. Locate and open the "Programs" settings.
   
   ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/9913912d-cbc4-464c-bd08-b983854f8912)
   - Once you have access, under "Programs and Features" select "Turn Windows features on or off".
    ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/c15b56d4-21b9-498b-b26e-e5a77f2c864b)
   - A dialog box will appear. Navigate to "Internet Information Services", and then click on the "+" symbol to view "World Wide Web Services".

   ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/73e99ed9-28c1-4f32-ae26-50f4cc56ebf4)

   - Once "World Wide Web Services" appears click on the "+" symbol to view "Application and Development Features".

   - Once again click on the "+" symbol to view more features under "Application and Development Features", and check the box for "CGI"
  
   - Once "CGI" is checked scroll down a bit until you see "Common HTTP Features" and check the box for that one aswell.
   
   ![image](https://github.com/Claudehub/osticket-prereqs/assets/159544351/d0b4e012-0d3b-4975-b045-dc050b7b3496)

5. **Install and Enable IIS:**

   - Click "OK" to install IIS with the selected features.

   *Note: You can verify the installation of IIS by opening a web browser on the virtual machine and navigating to "127.0.0.1". You should see a default web page if IIS is installed and running correctly.* 

6. **Install PHP Manager for IIS and Rewrite Module:**
   - Download and install PHP Manager for IIS ([PHPManagerForIIS_V1.5.0.msi](https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view)) from the [Installation Files](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) and follow the installation wizard to complete the installation.
   - Download and install Rewrite Module ([rewrite_amd64_en-US.msi](https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view)) and follow the installation wizard to complete the installation.

7. **Create PHP Directory and Install PHP:**
   - Create a folder named "PHP" in the C drive (C:\PHP).
   
   - Download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) from the Installation Files.
   
   - Extract the contents of the downloaded zip file into the C:\PHP directory.

8. **Install VC_redist.x86.exe:**
   - Download VC_redist.x86.exe from the Installation Files.
   
   - Run the downloaded file and follow the setup wizard to complete the installation.

9. **Install MySQL:**
   - Download MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the Installation Files.
   
   - Run the downloaded file and follow the setup wizard:
     - Choose Typical Setup.
     - Launch Configuration Wizard after install.
     - Choose Standard Configuration.
     - Set the root password to "Password1".
     - Execute the process.
!! ATTENTION !! If this appears, choose to “Keep” the file:

10. **Configure IIS:**
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
