# Azure SIEM Project

<br>

# Introduction


In the modern era of technology, companies are heavily relying on their IT infrastructure in order to do their everyday tasks. And of course in the world of technology, it is important that companies are up to date on their security. Companies use SIEM (Security Information and Event Management) tools to monitor suspicious events within the work environment. In today’s era, SIEM tools are in higher demand due to cybersecurity threats evolving day by day. These tools allow security professionals to perform real-time analysis of the IT infrastructure and monitor the overall health of machines within an organization.

In this project, I created a VM from Azure and used it as a honeypot to expose it to the world for attackers to discover it. I collected log data from the VM by using a PowerShell Script and a Third-Party Geographic Data API and transferred that data back to Azure to create a map of the attacks from around the world. I then was able to analyze where the attacks were coming from and take note of the number of failed login attempts from different regions.

<br>
<br>


# Purpose
The purpose of this project was to learn the basics of Azure SIEM tools and use them to track down malicious attackers from around the globe. I have documented all the steps I have taken in order to successfully complete this project.


<br>
<br>
<br>


# Tools used for this project

- Microsoft Azure
- Microsoft Sentinel
- Log Analytics Workspace
- Windows 10 OS
- Windows PowerShell ISE
- PowerShell Script (from Josh Madokor)
- Third Party Geographic API: https://www.ipgeolocation.io

<br>
<br>
<br>

# Creating Virtual Machine:

I created an Azure virtual machine and chose Windows 10 as my image. I intentionally made this VM vulnerable and used it as a honeypot to attract attackers from all over the world. 
<br>
<br>

![1](https://github.com/obi298/Azure-SIEM-Project/assets/90945162/72d5bfba-542e-480c-8307-f9046a647748)

<br>
<br>
<br>



# Configuring VM Security Rules:
<br>

I created a username and password that was used to login to the virtual machine. I also set the RDP to port 3389 in order for the virtual machine to be exposed to attackers.
<br>
<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/2af7b607-c5cd-43ac-a0cc-ff04f3608f46" alt="Azure Network Security Rule" width="600" height="550">


<br>
<br>
<br>


I added a new security group and configured the network settings to make the virtual machine vulnerable and discoverable to attackers. The virtual machine was used as a honeypot to attract attackers from all over the world.

<br>
<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/9ce135bf-fa73-445e-a665-0dd08f91a63a" alt="Azure Network Security Rule" width="600" height="500">

<br>
<br>
<br>

I deleted the old inbound security rule and added a new one. The new rule allowed the virtual machine to be exposed to attackers. 


![5](https://github.com/obi298/Azure-SIEM-Project/assets/90945162/50a0788e-d3b6-474d-9e40-a526c051b8ed)

 <img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/2f24f0ef-afd9-4ac9-a7dd-f832de90a293" alt="Azure Network Security Rule" width="450" height="500">

<br>
<br>
<br>

Here, I created a new log analytics workspace. 


<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/38d0b709-fb87-4121-9306-a61f424f283e" alt="Log Analytics Workspace" width="600" height="550">

<br>
<br>
<br>


I went to the settings and enabled data collection for all events which allowed the virtual machine to capture data from attacks.


![12](https://github.com/obi298/Azure-SIEM-Project/assets/90945162/856033db-ad15-44cb-aabd-11514a9d131a)

<br>
<br>
<br>



I connected the new workspace to the VM, which allowed Azure to capture log data from the VM.

<br>
<br>
<br>

 <img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/c8c5bf20-d2d3-48a8-ae9b-0cee90c46952" alt="" width="620" height="420">

<br>
<br>
<br>

 I was able to set up Microsoft Sentinel as a SIEM tool to create a map of the attacks from around the world. After that, I added Sentinel to my log analytics workspace.
 
<br>
<br>

  <img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/84ff3d32-86c1-4087-87ae-761d659e8b78 " alt="" width="650" height="500">


<br>
<br>


After connecting Sentinel to my log analytics workspace, I used my public IP address to connect to the VM using RDP. 

<br>
<br>

 <img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/3defdbb1-1424-4512-96c9-b44025dfa44f" alt="" width="550" height="350">

 <br>
 <br>
 <br>

Before logging into the virtual machine, I purposefully made a few failed login attempts in order for them to be viewed as logs in Windows Event Viewer.
<br>
<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/52f61920-496c-400e-9475-86f7d62b8a60" alt="" width="400" height="350">

<br>
<br>
<br>

After successfully logging into the VM, I went to Windows Event Viewer. I was able to see my failed event logs.  

<br>
<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/51ef50d9-aa25-454e-a255-787b64e43e5d" alt="" width="550" height="450">

<br>
<br>
<br>

I decided to click on one of the logs to get for information. Each log contains information such as event ID, failure reason, and network information.


 <img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/087f1b18-1468-4601-90fa-cfdda3a7f9d7" alt="" width="550" height="650">




