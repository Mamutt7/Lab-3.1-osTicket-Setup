# Lab-3.1-osTicket-Setup
In this lab I will be installing and setting up osTicket using an Azure windows VM to later showcase and practice my admin and user skills.

Create an Azure Virtual Machine Windows 10, 4 vCPUs
-	Name: osticket-vm
-	Username: labuser
-	Password: osTicketPassword1!

Log into the VM with Remote Desktop

Within the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
-	We will use the files in this folder to install osTicket and some of the dependencies.

Install / Enable IIS in Windows WITH CGI
-	World Wide Web Services -> Application Development Features -> [X] CGI ![image](https://github.com/user-attachments/assets/7dc7cd1e-2a26-4b2b-bf7d-6bb721a0917e)

 

From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi) ![image](https://github.com/user-attachments/assets/82d4fbb2-7b27-4dec-bde2-b1eb3b955c56)


 

Create the directory C:\PHP

From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.

From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
-	Typical Setup ->
-	Launch Configuration Wizard (after install) ->
-	Standard Configuration ->
-	Username: root
-	Password: root ![image](https://github.com/user-attachments/assets/98694b9b-5135-4060-bc5c-25bbae30d022) ![image](https://github.com/user-attachments/assets/f2fd4b36-8754-4115-bf33-7621e90400db)


 
 

Open IIS as an Admin

Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

Reload IIS (Open IIS, Stop and Start the server) ![image](https://github.com/user-attachments/assets/8903891c-5207-4e23-8db5-16b054bc127a)

 

Install osTicket v1.15.8
-	From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
-	Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”
！! ATTENTION !! When you get to the step when you're putting the "osTicket" folder inside of "c:\inetpub\wwwroot", make sure it's named exactly "osTicket" with no spaces. If it's not named correctly or has a space, you'll get a "404 page not found" at the very end of the lab :) Good luck. ![image](https://github.com/user-attachments/assets/a6deb705-b040-4d2e-84e3-3df38573efee)


 

Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket
-	On the right, click “Browse *:80” ![image](https://github.com/user-attachments/assets/5dd3ad37-3c6a-44df-8507-84ac781b1e25)


 

Note that some extensions are not enabled
-	Go back to IIS, sites -> Default -> osTicket
-	Double-click PHP Manager
-	Click “Enable or disable an extension”
-	Enable: php_imap.dll
-	Enable: php_intl.dll
-	Enable: php_opcache.dll
-	Refresh the osTicket site in your browser, and observe the changes ![image](https://github.com/user-attachments/assets/339a5e34-91a5-425c-ad1d-0e237546eef3) ![image](https://github.com/user-attachments/assets/d3d1fd8c-b238-441f-9af6-57d599fdf757)



 
 

Rename: ost-config.php
-	From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
-	To: C:\inetpub\wwwroot\osTicket\include\ost-config.php ![image](https://github.com/user-attachments/assets/d0c73f6e-5eb6-43d7-bc10-b5a931a6a5e5)


 

Assign Permissions: ost-config.php
-	Disable inheritance -> Remove All
-	New Permissions -> Everyone -> All ![image](https://github.com/user-attachments/assets/0b6dae00-7939-48b7-8195-da8f01e9aa42) ![image](https://github.com/user-attachments/assets/d1cba096-b86b-4014-a210-9994f2b738b7)



 

 
(Here I forgot to add “Full Control” Access initially, so I was getting an error when hitting continue on the osTicket installer)

Continue Setting up osTicket in the browser (click Continue)
-	Name Helpdesk
-	Default email (receives email from customers) ![image](https://github.com/user-attachments/assets/cbc952f9-c638-4884-9aec-418cd252cbda)


 

From the “osTicket-Installation-Files” folder, install HeidiSQL.
-	Open Heidi SQL
-	Create a new session, root/root
-	Connect to the session
-	Create a database called “osTicket” ![image](https://github.com/user-attachments/assets/75461acc-ed86-48f3-908c-7445d473c420)


 

Continue Setting up osTicket in the browser
-	MySQL Database: osTicket
-	MySQL Username: root
-	MySQL Password: root
-	Click “Install Now!” ![image](https://github.com/user-attachments/assets/e37438f7-9617-4072-9866-3e3a61030e76) ![image](https://github.com/user-attachments/assets/11ecc5ea-ff67-4870-9727-90e9902f2a80)



 

 
(Here I hit refresh on osTicket and a big table of data populated)

Congratulations, hopefully it is installed with no errors!
-	Browse to your help desk login page: http://localhost/osTicket/scp/login.php ![image](https://github.com/user-attachments/assets/0a1204e0-dd8e-41b5-9f0b-f2e4cbe96d49)


 

End Users osTicket URL:
-	http://localhost/osTicket/ ![image](https://github.com/user-attachments/assets/dbe09db6-b0a5-44e2-b119-2611b7a46093)


 
