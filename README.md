<p align="center">
<img src="https://i.imgur.com/KzJbWRS.png" height="45%" width="45%" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system "osTicket" within a created virtual machine using Microsoft Azure.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- MySQL / Heidi SQL
- osTicket: Support Ticketing System

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure basic fundamentals (<a href="https://github.com/JTYKolesar/azure-start#-create-a-resource-group">Guide</a>)
- Azure Virtual Machine running Windows OS
- Installation Files within VM (<a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Download All</a>):
  - <a href="https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view">PHP Manager for IIS v1.5.0</a>
  - <a href="https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view">Rewrite Module</a>
  - <a href="https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view">PHP v7.3.8 NTS</a>
  - <a href="https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view">Microsoft Visual C++ Redistributable</a>
  - <a href="https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view">MySQL v5.5.62</a>
  - <a href="https://www.heidisql.com/installers/HeidiSQL_12.3.0.6589_Setup.exe">HeidiSQL v12.3.0.6589</a>

<h2>Installation Steps</h2>

<h3>Part 1: Creating and Connecting to a Virtual Machine in Azure</h3>

- Create a "Resource Group".
- Create a "Virtual Machine" running Windows OS with an adequate Size.
  - _This example uses Virtual Machine named `osTicket-VM`, with username `ostuser`, Size `4 vCPUs`_
- Connect to that VM using Remote Desktop Connection (RDP).

_If you don't know how to complete this prerequisite, refer to <a href="https://github.com/JTYKolesar/azure-start#-create-a-virtual-machine">THIS PAGE</a>_

<h3>Part 2: Enabling Windows Features in the Virtual Machine</h3>

- Before installing any file, on the virtual machine:
  - Press the Windows Key/Button, then search for "Turn Windows Features on or off /Control Panel".
<p align="center">
<img src="https://i.imgur.com/8NCudlF.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

- Find "Internet Information Services", then click the checkbox ☐ to enable it (should now have a small black box in the middle, NOT a checkmark).
  - Then, expand the folder by clicking the [+] button next to it.
- Expand "Application Development Features", then checkmark "CGI".
- Expand "Common HTTP Features", then checkmark ALL boxes.
- Click "OK" to apply changes.
<p align="center">
<img src="https://i.imgur.com/vTX7c7x.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/FYHztm2.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

_With those changes applied, we'll need to confirm if they are working._
- Open Microsoft Edge browser (or any other browser).
- On the address bar, type in "127.0.0.1", then ENTER.

_This should take you to the "Internet Information Services" page, which confirms the features are working._
<p align="center">
<img src="https://i.imgur.com/uzusaWg.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h3>Part 3: Installing osTicket: Support Ticketing System</h3>

_We'll now need to install the prerequisites files onto the virtual machine in order for osTicket to run correctly._ </br>
_You can download all of the necessary files <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">HERE</a>_. (Must be on the Virtual Machine!)
<p align="center">
<img src="https://i.imgur.com/z2pjEZI.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- On the virtual machine, first install <a href="https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view">PHPManagerForIIS_V1.5.0.msi</a> (PHP Manager for IIS).
- When the installation prompt appears, click "Next" > Select "I Agree" and "Next" > After installation, "Close".
<p align="center">
<img src="https://i.imgur.com/nUge8wP.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- Next, install <a href="https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view">rewrite_amd64_en-US.msi</a> (Rewrite Module)
- When the installation prompt appears, click the checkbox to Agree the terms > click "Install" > After installation, "Finish".
<p align="center">
<img src="https://i.imgur.com/xrSD9NW.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

_We're going to have to create a directory for the next installation:_
- Open the `C:\` drive in "Windows Explorer".
- Right-click on an empty space and select to "New" > "Folder" to create a blank folder.
- Rename the folder to "PHP".
  - _You can right-click the new folder and select "Rename", or slowly double-click it to allow renaming_
<p align="center">
<img src="https://i.imgur.com/5yEsn7Z.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- Download <a href="https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view">php-7.3.8-nts-Win32-VC15-x86.zip </a> (PHP)
  - You'll notice that the file is contained in a .zip file, so we'll have to extract the contents from it before using._
- Right-click on the .zip file > click "Extract All..." > "Browse" > Find and select the PHP folder in C:\ > "Extract".
  - _Or you can simply type it in the box if you already know the path name._
<p align="center">
<img src="https://i.imgur.com/ZfLqf3M.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/6SEcPHm.jpg" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>

