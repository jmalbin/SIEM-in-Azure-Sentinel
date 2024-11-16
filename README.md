# SIEM-in-Azure-Sentinel

<h2>Description</h2>
In this lab, I created a Security Incident and Event Management (SIEM) using Microsoft Azure and used it to identify and log failed login attempts through a Remote Desktop.  By exposing the virtual machine to the Internet, I have created a honeypot in order to track login attempts from across the world.  With Azure Sentinel and KQL, I am able to take a log file from a script and map all the attack attempts across the world.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Azure Portal</b> 
- <b>Azure Sentinel</b>
- <b>PowerShell</b>
- <b>Kusto Query Language (KQL)</b> 
- <b>Network Security Groups</b>

<h2>Environments Used </h2>

- <b>Windows 10</b>

<h2>Program walk-through:</h2>

<p align="center">
1. I started by creating a virtual machine, which will act as a honeypot for potential attackers, and a log analytics workspace to format the collected information in a way that can be easily read.  They are stored in the Honeypotlab resource group. <br/>
<img src="https://i.imgur.com/AOWMz5s.png" height="80%" width="80%" alt="File Integrity Monitor Steps"/>
<br />
<br />
2. Inside the virtual machine, I ran a script in PowerShell that will identify failed login attempts through RDP and add them to a log file titled failed_rdp.log.  <br/>
<img src="https://i.imgur.com/jhcjFzS.png" height="80%" width="80%" alt="File Integrity Monitor Steps"/>
<br />
<br />
3. This is the inside of the log file.  It includes a list of sample attacks to show how the format should look.  At the bottom, you can see a login attempt from jmalbin, which was a failed login attempt shown in the previous step that I made to test that it had worked. <br/>
<img src="https://i.imgur.com/oReOa1F.png" height="80%" width="80%" alt="File Integrity Monitor Steps"/>
<br />
<br />
4. With the firewall disabled on the virtual machine, it is more vulnerable from potential attacks.  I took an hour break, and noticed that several login attempts from Germany were attempted.  <br/>
<img src="https://i.imgur.com/kdecOPe.png" height="80%" width="80%" alt="File Integrity Monitor Steps"/>
<br />
<br />
5. Next, I used the failed_rpd.log file in the Log Analytics workspace and ran a script in order to display the collected information in a way that is much easier to read.  There are now fields for the timestamp, location, source and destination, latitude and longitude, and more.  <br/>
<img src="https://i.imgur.com/pnPrs8U.png" height="80%" width="80%" alt="File Integrity Monitor Steps"/>
<br />
<br />
6. Using Azure Sentinel, I ran the script above in order to only gather the information about the attackers' geolocation.  With the essential information trimmed down, I am now able to map the location of failed connection attempts.  Now, the only thing to do is wait and see the map fill up over time.  <br/>
<img src="https://i.imgur.com/HDFn83N.png" height="80%" width="80%" alt="File Integrity Monitor Steps"/>
<br />
<br />
7. Several hours later, the map is now looking much more filled out.  <br/>
<img src="https://i.imgur.com/F8CYIwT.png" height="80%" width="80%" alt="File Integrity Monitor Steps"/>
</p>
