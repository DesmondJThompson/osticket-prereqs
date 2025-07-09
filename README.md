<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Download and extract osTicket-Installation-Files.zip
- Install and enable IIS with CGI
- Install PHP Manager for IIS
- Install IIS Rewrite Module
- Install MySQL
- Install HeidiSQL

<h2>Installation Steps</h2>

Step 1: Set Up a Windows 10 VM (Optional)

- Use Azure, VirtualBox, or a local setup

- Ensure the system is updated to version 21H2 or newer

- Enable Remote Desktop access (if using Azure or remote)

Step 2: Start by downloading and extracting [osTicket-Installation-Files.zip](https://github.com/DesmondJThompson/osticket-prereqs/releases/download/setup-files-v1/osTicket-Installation-Files.zip) to your Desktop.

Step 3: Install and Enable IIS
Go to Control Panel > Programs > Turn Windows features on or off

Enable:

- Internet Information Services

- Application Development Features > CGI

- Web Management Tools

<img width="422" alt="Screenshot 2025-07-06 at 9 00 45 AM" src="https://github.com/user-attachments/assets/71d27e55-2092-4e0c-9d92-5f435ec6b901" />
 
 Step 3: Install PHP Manager for IIS
From the "osTicket-Installation-Files" folder, run PHPManagerForIIS.msi

- Follow installation prompts

<img width="870" alt="Screenshot 2025-07-06 at 9 43 39 AM" src="https://github.com/user-attachments/assets/348e9584-f934-4968-955c-8436ac8e7a28" />

Step 4: Install Rewrite Module
- Run rewrite_amd64_en-US.msi from the "osTicket-Installation-Files" folder

- Follow installation prompts
(This is required for osTicket to handle clean URLs) 

<img width="495" alt="Screenshot 2025-07-06 at 9 45 43 AM" src="https://github.com/user-attachments/assets/022de829-14fa-4087-8bc9-b08d395c8640" />

Step 5: Set Up PHP
- Create folder: C:\PHP

- Unzip: php-7.3.8-nts-Win32-VC15-x86.zip → into C:\PHP
<img width="813" alt="Screenshot 2025-07-06 at 9 46 47 AM" src="https://github.com/user-attachments/assets/cea8e2a3-9589-4fdf-a88e-d6157a64890f" />
<img width="924" alt="Screenshot 2025-07-06 at 9 47 41 AM" src="https://github.com/user-attachments/assets/11eaf96c-6334-456b-893b-ab846a831912" />

Step 6: Install Visual C++ Redistributable VC_redist.x86.exe from "osTicket-Installation-Files" folder
<img width="480" alt="Screenshot 2025-07-06 at 9 49 03 AM" src="https://github.com/user-attachments/assets/d792e3ca-d151-4a46-b02f-9713bf9c76c3" />
der
- Follow the installation prompts

Step 7: Install MySQL 5.5 from "osTicket-Installation-Files" folder
Run: mysql-5.5.62-win32.msi

- Choose: Typical Setup

- After install: Launce Configuration Wizard

- Choose: Standard Configuration
  
- Set your username and password
  
- Follow the installation prompts

<img width="496" alt="Screenshot 2025-07-06 at 9 50 48 AM" src="https://github.com/user-attachments/assets/bba79dd5-499b-4bad-a9ee-01aff979a0ce" />
<img width="494" alt="Screenshot 2025-07-06 at 9 51 01 AM" src="https://github.com/user-attachments/assets/22192983-db16-481a-a692-06938a850426" />
<img width="501" alt="Screenshot 2025-07-06 at 9 51 59 AM" src="https://github.com/user-attachments/assets/64f3d74c-1b63-4684-b404-25a42822cd94" />
<img width="498" alt="Screenshot 2025-07-06 at 9 53 10 AM" src="https://github.com/user-attachments/assets/255dcb9b-1de2-4fd7-9167-7dba74df7f9b" />

Step 8: Configure IIS with PHP

- Open IIS as Administrator

- Go to: PHP Manager > Register new PHP version

- Register: C:\PHP\php-cgi.exe

- Restart IIS (Stop → Start the server)

<img width="783" alt="Screenshot 2025-07-06 at 9 54 14 AM" src="https://github.com/user-attachments/assets/444ba83d-df4d-41ed-87b0-ddb829836039" />
<img width="946" alt="Screenshot 2025-07-06 at 10 04 38 AM" src="https://github.com/user-attachments/assets/0388f7d3-6877-47ee-b94f-358ebc107d96" />
<img width="946" alt="Screenshot 2025-07-06 at 10 04 51 AM" src="https://github.com/user-attachments/assets/01c13dab-bd7a-48e6-82f2-694706260c6d" />

Step 9: Install osTicket

- Unzip osTicket-v1.15.8.zip

- Copy the upload folder into C:\inetpub\wwwroot

- Rename upload to osTicket
<img width="1118" alt="Screenshot 2025-07-06 at 10 10 23 AM" src="https://github.com/user-attachments/assets/bd6c38b6-f66c-4977-bd3e-a9371aa3142c" />
<img width="846" alt="Screenshot 2025-07-06 at 10 12 58 AM" src="https://github.com/user-attachments/assets/c1c5c8d0-b2f5-4585-bb04-95ca845e5dc1" />
<img width="848" alt="Screenshot 2025-07-06 at 10 13 24 AM" src="https://github.com/user-attachments/assets/f839687d-68cf-4ac2-8730-1badc9032683" />

Step 10:  Launch osTicket in Browser
- In IIS: Go to Sites > Default Web Site > osTicket

- On the right: click *“Browse :80”

- You should now see the osTicket installer in your browser.
<img width="605" alt="Screenshot 2025-07-06 at 10 26 17 AM" src="https://github.com/user-attachments/assets/012258a6-98e7-4790-a27d-3827e2d8f2ef" />

Step 11: Enable PHP Extensions
In IIS:

- Go to Sites > Default > osTicket > PHP Manager

- Click “Enable or disable an extension”

Enable the following:

- php_imap.dll

- php_intl.dll

- php_opcache.dll

Refresh the browser to see warnings disappear
<img width="795" alt="Screenshot 2025-07-06 at 10 29 34 AM" src="https://github.com/user-attachments/assets/b88134db-f7f6-40c6-b6b9-464b84d9bef0" />
<img width="1024" alt="Screenshot 2025-07-06 at 10 30 37 AM" src="https://github.com/user-attachments/assets/bb00355b-8a48-400c-a1cc-580804fac581" />
<img width="621" alt="Screenshot 2025-07-06 at 10 33 13 AM" src="https://github.com/user-attachments/assets/3fdd7090-5135-43e5-8a30-7982e6072133" />

Step 12: Configure ost-config.php
Rename: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
➡️ ost-config.php

Set permissions:

- Right-click → Properties > Security

- Disable inheritance → Remove all

- Configure new permissions

<img width="833" alt="Screenshot 2025-07-06 at 10 36 47 AM" src="https://github.com/user-attachments/assets/e4595bb7-e2e9-473b-921d-9ca83e37b012" />
<img width="856" alt="Screenshot 2025-07-06 at 10 38 13 AM" src="https://github.com/user-attachments/assets/4ecbeb40-60dc-4a62-ac7a-b79d9e6161aa" />
<img width="361" alt="Screenshot 2025-07-06 at 10 38 42 AM" src="https://github.com/user-attachments/assets/2296c3b2-1fa5-4a79-be84-ab3ed1030738" />
<img width="768" alt="Screenshot 2025-07-06 at 10 41 37 AM" src="https://github.com/user-attachments/assets/91d3b61f-6801-49de-b5c5-f1185e2251b4" />
<img width="524" alt="Screenshot 2025-07-06 at 10 41 49 AM" src="https://github.com/user-attachments/assets/fddb2624-9ae2-4d0a-b755-b8d5c0123a2c" />
<img width="868" alt="Screenshot 2025-07-06 at 10 48 06 AM" src="https://github.com/user-attachments/assets/6561fa9b-c1a7-45df-b800-b8307e473776" />

Step 13: Install HeidiSQL & Create Database

- Install: HeidiSQL.exe from "osTicket-Installation-Files"

- Create new session:

- Host: localhost

- Input Username and Password

- Connect and create a database called osTicket

<img width="596" alt="Screenshot 2025-07-07 at 7 32 37 PM" src="https://github.com/user-attachments/assets/d98d3600-2e55-4b45-9a79-3cd201e6056a" />
<img width="685" alt="Screenshot 2025-07-07 at 7 33 23 PM" src="https://github.com/user-attachments/assets/5c7f9923-bdca-4301-9970-0377a96d7d0b" />
<img width="684" alt="Screenshot 2025-07-07 at 7 33 44 PM" src="https://github.com/user-attachments/assets/2be58651-c00f-410a-ba9b-d0a7be217e2f" />
<img width="933" alt="Screenshot 2025-07-07 at 7 35 35 PM" src="https://github.com/user-attachments/assets/ddc22c8d-7c48-44d8-830b-31e0b3581ea4" />

Step 14: Finish osTicket Web Setup

Back in the browser:

- Continue installer

Set:

- Helpdesk name

- Admin email

- MySQL DB: osTicket

- Input Username and Password

Click: Install Now
<img width="1161" alt="Screenshot 2025-07-07 at 7 23 35 PM" src="https://github.com/user-attachments/assets/bc374d43-c19e-437b-895d-0bffbf2cb1f1" />
<img width="1423" alt="Screenshot 2025-07-07 at 7 37 36 PM" src="https://github.com/user-attachments/assets/9eb60334-feb3-4e1d-ae6f-905c4ea247ba" />
<img width="1416" alt="Screenshot 2025-07-07 at 7 38 04 PM" src="https://github.com/user-attachments/assets/8d6e9e38-17f0-4b02-8898-29d976bd0c57" />

🎉 You're Done!

- Admin Login: http://localhost/osTicket/scp/login.php

- End User Portal: http://localhost/osTicket/
