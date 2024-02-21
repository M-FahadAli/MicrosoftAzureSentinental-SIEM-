<h1>Microsoft Azure: Azure Sentinel (SIEM & SOAR) Project</h1>
<img src="https://img.hotimg.com/Image-2024-02-20-at-2.19PM.jpeg" alt="Image-2024-02-20-at-2.19PM.jpeg" border="0" /> 
<h2>Description</h2>
Using Azure Sentinel, I monitor a live honeypot VM for RDP brute force attacks worldwide. A custom PowerShell script fetches attackers' geolocation data, visualized on Azure Sentinel Map for proactive threat response.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Microsoft Azure</b>
- <b>Remote Desktop Connection</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Establish a virtual machine (VM) configured to allow unrestricted traffic access, facilitating its discovery by any source: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.24.51PMd203487f7546f3f6.png" alt="Screenshot-2024-02-20-at-2.24.51PMd203487f7546f3f6.png" border="0" />
<br />
<br />
Modify the inbound rules of the security group to enhance the discoverability of the VM:  <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.25.50PM.png" alt="Screenshot-2024-02-20-at-2.25.50PM.png" border="0" />
<br />
<br />
Establish a Log Analytics Workspace dedicated to logging inbound traffic directed towards the VM: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.27.36PM.png" alt="Screenshot-2024-02-20-at-2.27.36PM.png" border="0" />
<br />
<br />
Establish a connection between the Log Analytics Workspace and the VM to enable logging of inbound traffic: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.27.41PM.png" alt="Screenshot-2024-02-20-at-2.27.41PM.png" border="0" />
<br />
<br />
Start the VM and establish a Remote Desktop Connection to access it: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.29.28PM.png" alt="Screenshot-2024-02-20-at-2.29.28PM.png" border="0" />
<br />
<br />
Disable the Windows Firewall on the VM accessed via Remote Desktop Connection:  <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.29.36PM.png" alt="Screenshot-2024-02-20-at-2.29.36PM.png" border="0" />
<br />
<br />
Check network connectivity by pinging the VM from your personal computer: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.29.42PM0d8fc77cbd2ada81.png" alt="Screenshot-2024-02-20-at-2.29.42PM0d8fc77cbd2ada81.png" border="0" />
<br />
<br />
Obtain an API key from ipgeolocation.io if you don't have one already: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.29.49PM.png" alt="Screenshot-2024-02-20-at-2.29.49PM.png" border="0" />
<br />
<br />
Execute a custom script on Windows PowerShell ISE, incorporating your API key, to retrieve geolocation data from attackers:  <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.29.54PM.png" alt="Screenshot-2024-02-20-at-2.29.54PM.png" border="0" />
<br />
<br />
Save the script output as a log file, generating a .txt file containing geolocation data for all failed login attempts: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.30.06PM.png" alt="Screenshot-2024-02-20-at-2.30.06PM.png" border="0" />
<br />
<br />
Develop a custom log file linked to the .txt file containing geolocation data for all failed login attempts: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.30.10PM.png" alt="Screenshot-2024-02-20-at-2.30.10PM.png" border="0" />
<br />
<br />
Utilize SQL queries within the logging system to analyze and observe the data retrieved from the custom log: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.30.27PM.png" alt="Screenshot-2024-02-20-at-2.30.27PM.png" border="0" />
<br />
<br />
Parse the raw custom logs to extract and retrieve the relevant fields:  <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.30.33PM.png" alt="Screenshot-2024-02-20-at-2.30.33PM.png" border="0" />
<br />
<br />
Ensure the accuracy of the custom fields before proceeding with any testing: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.30.36PM.png" alt="Screenshot-2024-02-20-at-2.30.36PM.png" border="0" />
<br />
<br />
Test the newly extracted custom fields to confirm if they successfully collect the required data:  <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.30.41PM.png" alt="Screenshot-2024-02-20-at-2.30.41PM.png" border="0" />
<br />
<br />
Set up Microsoft Sentinel: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.31.11PM.png" alt="Screenshot-2024-02-20-at-2.31.11PM.png" border="0" />
<br />
<br />
In Microsoft Sentinel, configure a map within workbooks utilizing longitude and latitude coordinates:  <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.31.16PM.png" alt="Screenshot-2024-02-20-at-2.31.16PM.png" border="0" />
<br />
<br />
Utilize the provided SQL query to filter and select the specific dataset for display. Then, apply the designated map settings to visualize the data on a world map, ensuring accurate representation and meaningful insights: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-9.50.50PM.png" alt="Screenshot-2024-02-20-at-9.50.50PM.png" border="0" />
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.31.30PM.png" alt="Screenshot-2024-02-20-at-2.31.30PM.png" border="0" />
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.31.36PM.png" alt="Screenshot-2024-02-20-at-2.31.36PM.png" border="0" />
<br />
<br />
Following a few hours, cyber attackers from around the world will likely discover the VM. At this point, you can monitor geolocation data to identify the origins of the breaches targeting your VM: <br/>
<img src="https://img.hotimg.com/Screenshot-2024-02-20-at-2.31.41PM.png" alt="Screenshot-2024-02-20-at-2.31.41PM.png" border="0" />
<br />
<br />
This marks the completion of the Microsoft Azure SIEM project! Remember, you have the option to adjust map settings to visualize additional custom fields.
<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
