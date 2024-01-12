 <h1>Vulnerability Management Home Lab</h1>


<h2>Description</h2>
In this lab we will cover vulnerability scanning and vulnerability remediation. These are two of the main steps in the Vulnerability Management Lifecycle. We will be using Nessus Essentials to scan local VMs hosted on VMWare Workstation in order run credentialed scans to discover vulnerabilities, remediate some of the vulnerabilities, then perform a rescan to verify remediation.
<br />


<h2>Utilities Used</h2>

- <b>Nessus</b> 
- <b>VMWare</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (22H2)

<h2>First Nessus Scan to The Virtual Machine walk-through:</h2>

<p>
Create virtual machine instance in VMWare:  <br/>
<img src="https://i.imgur.com/GMU6LES.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Ensure connectivity by pinging the virtual machine with your local machine:  <br/>
<img src="https://i.imgur.com/n633l78.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
With Nessus on local host, create a new scan: <br/>
<img src="https://i.imgur.com/kNHXIFY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/HkGci9v.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Enter in the name of scan and the target IP of the scan select the save option on the bottom left:  <br/>
<img src="https://i.imgur.com/GzDGbNw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We will be able to see the scan you created in the My Scans table. Start the scan by clicking the launch button indicated in the screen shot below:  <br/>
<img src="https://i.imgur.com/tWc7yuD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click on the name of the scan. This will bring us to the the results of the scan for us to further inspect:  <br/>
<img src="https://i.imgur.com/FpUVhtD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<h2>First Scan Description</h2>
For further inspection, we are able to take a deep dive in what the scan found. The vulnerabilities are organized on criticality. By clicking on a vulnerabily in the Vulnerabilies tab we are able to research deeper into what is found.
<br />
<br />



<h2>Second Nessus scan walk-through:</h2>
Next-up:
Setup the virtual machine to be able to accept authenticated scans. Provide credentials to Nessus then rescan the virtual machine to compare results with the new scans compared to the one shown on the first scan.
<br />
<br />
<p>
In the Virtual Machine, enable remote registry (this will allow the scanner to connect to this Virtual Machine's registry and look for unsecure configurations):  <br/>
<img src="https://i.imgur.com/4UA2A8t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
For the Advance Sharing Settings in the VM, make sure that the file and printer share is on:  <br/>
<img src="https://i.imgur.com/j01cO02.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Disable the notification for the User Account Control in the VM. (Only for this project but THIS IS NEVER A GOOD THING TO DO!):  <br/>
<img src="https://i.imgur.com/t5OzLmp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In the virtual machine, open the registry and add the key to allow the remote account to connect in: <br />
In this example created a new DWORD at the address in the Registry Editor and made its value set to 1 (see screenshot below) <br/>
<img src="https://i.imgur.com/V7fcTSP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
With this setup, we are ready to restart, login, and scan the virtual machine.  <br/>
<br />
<br />
 
Back in the Nessus interface we configure the scan by adding in the credentials of the VM to the scan:  <br/>
<img src="https://i.imgur.com/bC5VWye.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/Em4m96i.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br />
With the scan settings updated we are now able to rerun the scan.
<br />
<br />
In the new update of the scan you are able to see that there is much more vulnerabilities reported back:  <br/>
<img src="https://i.imgur.com/bW3AN9n.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br />
Since the scan was able to crawl through more of the VM, it was able to give us more feed back to what could be potentially harmful.<br />
<br />
<br />
</p>

<h2>Lessons Learned</h2>

- <b>The loop process of scanning and remediating to manage vulnerabilities</b>
- <b>A credential scan is will give us more feedback and alerts for us to dig into and remediate</b> 
<br />

<h2>Brush Up</h2>

- <b>Vulnerability Management on a large scale </b>
- <b>Touch up on CVSS scoring. </b>
- <b>Third Party Patching, Windows OS Patching that are setup, tested and deployed regularly (prevents going through and dealing with individual vulnerbilities that could be easily fixed by automated patching</b>
<br />

<h2>Shortcuts Learned</h2>

- <b>appwiz.cpl - Programs and features</b> 


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
