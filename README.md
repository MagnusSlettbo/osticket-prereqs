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

- Install and Enable IIS (Internet Information Services)
- Install PHP Manager for IIS
- Install Rewrite module
- Download PHP 7.3.8 and unzip into c:\PHP
- Install VC_redist.x86
- Install MySQL
- Download osTicket

<h2>Installation Steps</h2>

<p>
<p>To enable "IIS" Follow this path ->Control Panel > Programs > Programs and Features > Turn Windows features on or off (left side of the screen). Then under "Internet Information Services" expand this and then expand "Web Managment Tools" to reveal "IIS Managment Consol" and click the check box to enable.</p>
Then go to "World Wide Web Services" then to "Application Development Features" and enable "CGI" and "Common HTTP Features" below and press "OK" it will then apply the changes and install required settings and you just have to wait untill it says "Windows completed the required changes" as shown below. Then to test if it works type "127.0.0.1" into a browser, if it doesnt work try and redo the first step.
<img src="https://i.imgur.com/ASio4Wv.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/kg6ePfB.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/cFOq7vu.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h2></h2>
<p>
After installing PHP Manager & Rewrite Module, Create  the directory C:\PHP. Download the PHP 7.3.8 file and extract the contents into C:\PHP folder
</p>
<p> <img src="https://i.imgur.com/To8Lm5x.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> </p>
<p> <img src="https://i.imgur.com/Bfvph7m.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> </p>
<p>
Now we are going to intall "VC_redist.x86" & "MySQL 5.5.62" and configure MySQL. When setting up MySQL, on "Choose Setup Type" pick "Typical" -> Install -> Select the box "Launch the MySQL Instance Configuration Wizard" -> Finish. 
  In the config Wizard select "Standard Configuration" -> Next -> Setup Password. -> Next -> Execute and wait for it to finish configuration and then click "Finish".
</p>
<br />

<h2></h2>
<p>
<img src="https://i.imgur.com/Aqwr7T0.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now open "IIS" as Admin and click on "PHP Manager" then navigate to "register PHP". 
</p>
<p>Here you need to point to the php-chi.exe file found in C:\PHP </p>
<img src="https://i.imgur.com/iiaN4WL.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<p>Now we need to go back to the main menu in "IIS" and Restart the server</p>
<img src="https://i.imgur.com/B4qAaeg.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />

<h2>Downloading osTicket and setting it up</h2>
<p>
Now we need to Download osTicket, Once downloaded extract the "upload" folder into c:\inetpub\wwwroot. Then rename upload folder to "osTicket". Then restart the IIS server once more.
</p>
<img src="https://i.imgur.com/js0lxsQ.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<p>
Now when u have reopend "IIS" on the left side on "Sites" drop down then the "Default Web Site" dropdown then click on "osTicket" then on the right side of "IIS" window click on "Browse *80".
</p>
<img src="https://i.imgur.com/6wsIk1v.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<p>
Now you should be able to see osTicket installer like shown below, Notice that some of the settings is disabled. To enable them go back to the "IIS" -> Sites -> Default -> osTicket and click on PHP Manager and click "enable or disagble an extention" at the bottom inside of PHP Manager.
</p>
<p><img src="https://i.imgur.com/EqadzEF.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/CAY5ehA.png" height="40%" width="40%" alt="Disk Sanitization Steps"/></p>

  Enable the following extention:
  - php_imap.dll
  - php_intl.dll
  - php-opcache.dll
  <p> Now refresh the page and see that they have been enabled. </p>
<br />

<p> Rename: ost-config.php </p>
<p> From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php </p>
<p> To: C:\inetpub\wwwroot\osTicket\include\ost-config.php </p>
<br />

<h2></h2>
<p>
Lets assign permissions in the ost-config.php file. Right click on the file Properties -> Security -> Advanced:
</p>
<p><img src="https://i.imgur.com/TI8CjHr.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<p> Now press the Disable inheritance to remove all the listed groups in the list, and add a new entry called "everyone" then click apply and done. </p>

<br />

<h2></h2>
<p>
  Now back to finish setting up osTicket in the browser, Click "Continue" under the list of settings. Then fill in the information in the form to create your own help desk and the Admin user for the help desk. once you have filled in the information press "Install Now"
<p> <img src="https://i.imgur.com/ALXVbK5.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/S6M4F5e.png" height="40%" width="40%" alt="Disk Sanitization Steps"/></p>
</p>

<h2></h2>
<p>
  Now that osTicket is up and running head to " http://localhost/osTicket/scp/login.php" and login with the admin account you just created. To create tickets to go "http://localhost/osTicket/" and click Submit ticket.
</p>
<img src="https://i.imgur.com/mKBjoDL.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<p>
  Now to clean up a little. Delete the osTicket Setup file (C:\inetpub\wwwroot\osTicket\setup) And set permission "Read only" for C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>

