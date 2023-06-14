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

<h3>Installing osTicket: Support Ticket System</h3>

- Before installing any file, on the virtual machine:
  - Press the Windows Key/Button, then search for "Turn Windows Features on or off /Control Panel".
<p align="center">
<img src="https://i.imgur.com/8NCudlF.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

- Find "Internet Information Services", then click the ☐ to enable it (should now have a small black box in the middle, NOT a checkmark).
  - Then, expand the folder by clicking the [+] button next to it.
- Expand "Application Development Features", then checkmark "CGI".
- Expand "Common HTTP Features", then checkmark ALL boxes.
- Click "OK" to apply changes.
<p align="center">
<img src="https://i.imgur.com/vTX7c7x.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/FYHztm2.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>

_With those changes applied, we'll need to confirm it they are working._
- Open Microsoft Edge browser (or any other browser).
- On the address bar, type in "127.0.0.1", then ENTER.

_This should take you to the "Internet Information Services" page, which confirms the features working as intended._
<p align="center">
<img src="https://i.imgur.com/8NCudlF.jpg" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/uzusaWg.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

