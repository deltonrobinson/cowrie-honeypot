<h1>Cowrie Honeypot Deployment & Testing</h1>

<h3>Description</h3>
Project consists of deploying a realistic honeypot in an isolated virtual environment, simulate internal attacks, and analyze attacker behavior. Using Cowrie and additional services (FTP, HTTP, SMB, MySQL), the honeypot was configured to mimic an enticing internal server to capture logs of simulated attacks for analysis.
<br>

<h3>Languages and Utilities Used</h3>

- <b>VMWare</b> 
- <b>Cowrie</b>
- <b>vsftpd</b>
- <b>Apache httpd</b>
- <b>Samba smbd</b>
- <b>MySQL</b>

<h3>Environments Used </h3>
- <b>Kali Linux</b>

<!------------------------------------------------------------------------------------------------------------------------------------------------------------------------>

<h1>Setup of Ubuntu Honeypot within VMWare Environment</h1>

<h2>Cowrie OpenSSH</h2>
<h3>Setting up the Cowrie SSH Honeypot</h3>
<p align="center">
Installing python virtual environment:<br>
<img src="https://i.imgur.com/4miRnKd.png" height="80%" width="80%" alt="Setting up Cowrie OpenSSH"/><br>
Adding a cowrie user to the honeypot:<br>
<img src="https://i.imgur.com/N10xVyd.png" height="80%" width="80%" alt="Setting up Cowrie OpenSSH"/><br>
Activating and Starting Cowrie:<br>
<img src="https://i.imgur.com/3UMcjcM.png" height="80%" width="80%" alt="Setting up Cowrie OpenSSH"/><br>
Setting the Honeypot password to 123456789 by editing userdb.txt:<br>
<img src="https://i.imgur.com/vbitZlC.png" height="80%" width="80%" alt="Setting up Cowrie OpenSSH"/><br>
</p>

<h2>Apache HTTP</h2>
<h3>Setting up HTTP Service</h3>
<p align="center">
Installing apache2:<br>
<img src="https://i.imgur.com/7aRDUlV.png" height="80%" width="80%" alt="Setting up HTTP Service"/><br>
Setting up the default HTML login page for the Honeypot:<br>
<img src="https://i.imgur.com/ibL9f6d.png" height="80%" width="80%" alt="Setting up HTTP Service"/><br>
<img src="https://i.imgur.com/Hdrv0ys.png" height="80%" width="80%" alt="Setting up HTTP Service"/><br>
</p>

<h2>Very Secure FTP (VSFTP)</h2>
<h3>Setting up the FTP Service</h3>
<p align="center">
Installing vsftpd:<br>
<img src="https://i.imgur.com/I8XDb6I.png" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
Editing vsftpd config:<br>
<img src="https://i.imgur.com/r6UYGSc.png" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
Adding new user ftpuser:<br>
<img src="https://i.imgur.com/0u4sPax.png" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
</p>

<h2>Samba SMB</h2>
<h3>Setting up the SMB Service</h3>
<p align="center">
Installing Samba SMBD:<br>
<img src="https://i.imgur.com/TLzYZ62.png" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
Setting the /srv/samba/public directory to 777 (full permissions for everyone within this directory), and creating payroll.txt:<br>
<img src="https://i.imgur.com/7sIhmBX.png" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
Viewing the status of the service:<br>
<img src="https://i.imgur.com/lWRx0Qj.png" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
</p>

<h2>MySQL</h2>
<h3>Setting up the SQL Service</h3>
<p align="center">
Installing MySQL And viewing status of the service:<br>
<img src="https://i.imgur.com/Apzp9xU.png" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
Creating a payroll database:<br>
<img src="https://i.imgur.com/DvEw157.png" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
</p>

<!------------------------------------------------------------------------------------------------------------------------------------------------------------------------>

<h1>Performing a Simple Attack on the Ubuntu Honeypot</h1>

<h2>Kali Workstation</h2>
<h3>Initial Attack of Honeypot</h3>
<p align="center">
Nmap scan of the Ubuntu Honeypot from the Kali Workstation:<br>
<img src="" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
Using Hydra to gain acess to the Honeypot through OpenSSH (Cowrie):<br>
<img src="" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
Using SSH to connect to the Honeypot using credentials obtained from Hydra, and navigating to a user's directory:<br>
<img src="" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
Using Hydra to gain access to the Honeypot through FTP (VSFTP):<br>
<img src="" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
Moving through the Honeypot and downloading sentitive files to the Kali Workstation:<br>
<img src="" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
Reviewing downloaded sentitive files within the Kali Workstation Attacker:<br>
<img src="" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
</p>

<h2>Reviewing Attack Logs</h2>
<h3>Cowrie OpenSSH Service</h3>
<p align="center">
Grep of failed login attempts on the Cowrie SSH Honeypot:<br>
<img src="" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
Grep of successful login attempts on the Cowrie SSH Honeypot (u/root | p/123456789):<br>
<img src="" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
</p>
<h3>VerySecureFTP Service</h3>
<p align="center">
Grep of login attempts on the honeypot’s vsftpd service. Multiple failed and one success (u/ftpuser | p/ftpsuer):<br>
<img src="" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
Grep of successful login and downloads of sensitive information from the FTP server:<br>
<img src="" height="80%" width="80%" alt="Setting up Honeypot (installing git python3-venv)"/><br>
</p>




<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
-->
