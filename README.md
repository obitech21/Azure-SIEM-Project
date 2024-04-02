# Azure SIEM Project

<br>

# Introduction


In the modern era of technology, companies are heavily relying on their IT infrastructure in order to do their everyday tasks. And of course in the world of technology, it is important that companies are up to date on their security. Companies use SIEM (Security Information and Event Management) tools to monitor suspicious events within the work environment. In today’s era, SIEM tools are in higher demand due to cybersecurity threats evolving day by day. These tools allow security professionals to perform real-time analysis of the IT infrastructure and monitor the overall health of machines within an organization.

In this project, I created a VM from Azure and used it as a honeypot to expose it to the world for attackers to discover it. I collected log data from the VM by using a PowerShell Script and a Third-Party Geographic Data API and transferred that data back to Azure to create a map of the attacks from around the world. I then was able to analyze where the attacks were coming from and take note of the number of failed login attempts from different regions.


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
<br>

# Creating Virtual Machine

I created an Azure virtual machine and chose Windows 10 as my image. I intentionally made this VM vulnerable and used it as a honeypot to attract attackers from all over the world. 
<br>
<br>

![1](https://github.com/obi298/Azure-SIEM-Project/assets/90945162/72d5bfba-542e-480c-8307-f9046a647748)

<br>
<br>
<br>
<br>


# Configuring VM Security Rules
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
<br>
<br>

# Observing Logs in Windows Event Viewer
<br>

After connecting Sentinel to my log analytics workspace, I used my public IP address to connect to the VM using RDP. 

<br>
<br>

 <img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/3defdbb1-1424-4512-96c9-b44025dfa44f" alt="" width="500" height="300">

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

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/51ef50d9-aa25-454e-a255-787b64e43e5d" alt="" width="600" height="500">

<br>
<br>
<br>
<br>

# Collect Geographic Data from IP Address
<br>
I decided to click on one of the logs to get for information. Each log contains information such as event ID, account name, failure information, and network information.


<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/087f1b18-1468-4601-90fa-cfdda3a7f9d7" alt="" width="550" height="650">

<br>
<br>
<br>

I took the IP address from the log and entered it in a 3rd party API in order to collect geographic data. I collected geographic information from this website: www.ipgeolocation.io. 

<br>

I was able to see information such as country, state, time zone, and currency. I used this information to create my own log and sent that log into my log analytics workspace. 

 <img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/c2a6d87b-2d23-4525-bf6a-77acabadd256" alt="" width="520" height="410">

 <br>
 <br>
 <br>
<br>

 # Configure Firewall Settings
 <br>

In this step, I turned off the firewall settings in order to make the VM more vulnerable to attackers. I made sure that the firewall was disabled from the domain, private, and public profile. I wanted to make the VM as vulnerable as possible in order for attackers to discover it.

<br>

 <img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/1cf3c530-70aa-42eb-8c40-00b1082fa77d" alt="" width="620" height="510">

<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/6b24c20a-b20f-4727-99ee-5c3aa5adf840" alt="" width="450" height="510">

<br>
<br>


After configuring the firewall settings, I tested the virtual machine's connectivity by pinging it from the local machine. I also tested the connection before configuring the firewall settings. The virtual machine was able to communicate with the local machine after disabling the firewalls.

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/9687b95b-331a-42a2-a538-3428f8316ec2" alt="" width="650" height="400">
<br>
<br>
<br>
<br>

# Collect Geographic Data from Attackers

<br>

I copied a PowerShell script from Josh Madokor that was used to collect geographic data from failed login event logs and create a log file.

<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/b09ce001-dab5-4009-8474-9dd8ffd955d5" alt="" width="700" height="450">

<br>
<br>
<br>

After copying the script, I pasted it on Powershell ISE.

<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/7a07b8ef-6f5f-4570-ba7a-85599f27296a" alt="" width="850" height="700">

<br>
<br>
<br>

I generated an API key from the 3rd party API in order for the script to work with the API.

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/247f8e0f-2716-4a06-befe-e216597af8e1" alt="" width="650" height="320">

<br>
<br>
<br>

Entering the API key in the PowerShell script allowed the script to collect geographic data from attackers that were attempting to login to the virtual machine.

<br>
<br>
<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/d7cb1af5-a279-4793-aea4-fcfc6b168ef5" alt="" width="770" height="320">

<br>
<br>
<br>

After entering the API key, I ran the PowerShell script. The script was able to collect data from the API and WIndows Event Viewer. After running the script, I noticed that each error log contained a username, sourcehost, and destination host. 

<br>
<br>
<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/55fbafa3-e80d-44cf-9204-83b7f7b890dc" alt="" width="700" height="520">

<br>
<br>
<br>

# Custom Log and Field Extraction
<br>
<br>

After executing the script, I copied the data from my virtual machine and pasted the data in a text document on my local machine. I then saved the data on my local machine and created a custom log in order to put the geographic data in my log analytics workspace.

<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/3d75da6c-22c3-472e-b86e-a6dcb0cb3431" alt="" width="600" height="520">

<br>
<br>
<br>

During the custom log creation, I noticed that the data was successfully parsed from the failed event log file. 

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/f2377aea-2cd2-46eb-a085-62dcf8d07ac5" alt="" width="600" height="520">
<br>
<br>
<br>

After completing the custom log setup, I ran the failed event log file in the KUSTO interpreter.

<br>
<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/e39bbb65-d839-44c9-8e8f-7ac9f1a4887c" alt="" width="700" height="420">

<br>
<br>

I clicked on one of the log entries and extracted each field from it.

<br>
<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/5443e888-2b74-4c76-bd19-85d1023bb3bc" alt="" width="700" height="400">

<br>
<br>
<br>

I highlighted the values from each field and labeled them. I also selected the correct field type before saving the extraction. Because latitude had a numeric value, the field type was set to numeric. 

<br>
<br>

 <img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/dc71d7b9-65f4-4f85-8f9e-ee4dc1f4939a" alt="" width="700" height="500">

<br>
<br>
<br>

After the latitude field, I repeated the same process for all of the other fields. 

<br>
<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/faec8c7f-2127-43ac-be99-d0c89f24baae" alt="" width="900" height="350">


<br>
<br>
<br>

# Attack Map Creation

After fully extracting all of the fields from the log data, I finally had everything setup to create an attack map. I first created a workbook from Microsoft Sentinel. In that workbook, I ran this query:

```
failed_rdp_geo_CL| summarize event_count=count() by sourcehost_CF, latitude_CF, longitude_CF, country_CF, label_CF, destinationhost_CF
| where destinationhost_CF != "samplehost" | where sourcehost_CF != ""
```
<br>
<br>
<br>

 <img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/0313972a-9299-4437-a5dc-7ad7927e57e0" alt="" width="980" height="480">

<br>
<br>
<br>

I then clicked on Visualization and changed it to "Map."

<br>
<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/411f3297-793d-4d9e-bf54-37bfba0f1522" alt="" width="550" height="490">

<br>
<br>
<br>

Finally, I made sure to put the right latitude, longitude, and label for the map. I noticed that the attacks on the map were coming from Russia and Brazil. I decided to wait a little more to see if more attacks would show up.

<br>
<br>
<br>


 <img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/4e4bf79e-fefc-4439-9537-d27e3de84805" alt="" width="850" height="500">

<br>
<br>
<br>

After waiting some time, I discovered that more attacks appeared on the map from different countries. 

<br>
<br>
<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/c8a62139-51b4-4a17-941c-6642d7d252e2" alt="" width="850" height="550">

<br>
<br>
<br>

After waiting again, I noticed even more attacks. 

<br>
<br>
<br>

<img src="https://github.com/obi298/Azure-SIEM-Project/assets/90945162/e61cf2a4-fd3f-4bc0-8eeb-0ababf4a6670" alt="" width="850" height="450">

<br>
<br>
<br>

That concludes my project.


# Conclusion

<br>

The purpose of this project was for me to gain hands-on experience with using SIEM tools. I learned the basics of using SIEM tools for real-time event analysis and advanced analytics. I also gained a better understanding of the services in Azure and how they can be used in real world scenarios.
 







