# Azure SIEM Project

<br>
<br>
<br>

# Introduction:


In the modern era of technology, companies are heavily relying on their IT infrastructure in order to do their everyday tasks. And of course in the world of technology, it is important that companies are up to date on their security. Companies use SIEM (Security Information and Event Management) tools to monitor suspicious events within the work environment. In today’s era, SIEM tools are in higher demand due to cybersecurity threats evolving day by day. These tools allow security professionals to perform real-time analysis of the IT infrastructure and monitor the overall health of machines within an organization.

In this project, I created a honeypot and exposed it to the world so that attackers can discover it.  I collected log data from the VM by using a PowerShell Script and a Third-Party API and transferred that data back to Azure to create a map of the attacks from around the world. I then was able to analyze where the attacks were coming from and take note of the number of failed login attempts from different regions.

<br>
<br>


# Purpose
The purpose of this project was to learn the basics of Azure SIEM tools and use them to track down malicious attackers from around the globe. I have documented all the steps I have taken in order to successfully complete this project.


<br>
<br>
<br>



# Creating Virtual Machine:

I created a virtual machine and chose Windows 10 as my image. I intentionally made this VM vulnerable so that it can be discoverable to the whole world. I used Windows 10 Pro as my Image. I also selected the region for my virtual machine. This virtual machine was used as a honeypot to attract attackers from all over the world. I used this VM to capture failed login events from attackers and collect global data.

![1](https://github.com/obi298/Azure-SIEM-Project/assets/90945162/72d5bfba-542e-480c-8307-f9046a647748)

<br>
<br>
<br>



# Configuring VM Security Rules:

I added a new security group and configured the network settings to make the virtual machine vulnerable and discoverable to attackers.

![3](https://github.com/obi298/Azure-SIEM-Project/assets/90945162/2af7b607-c5cd-43ac-a0cc-ff04f3608f46)


![4](https://github.com/obi298/Azure-SIEM-Project/assets/90945162/9ce135bf-fa73-445e-a665-0dd08f91a63a)

<br>
<br>
<br>

I deleted the old inbound security rule and added a new one. The new rule allowed the virtual machine to be exposed to attackers. 


![5](https://github.com/obi298/Azure-SIEM-Project/assets/90945162/50a0788e-d3b6-474d-9e40-a526c051b8ed)

![6](https://github.com/obi298/Azure-SIEM-Project/assets/90945162/2f24f0ef-afd9-4ac9-a7dd-f832de90a293)

<br>
<br>
<br>

Here, I created a new log analytics workspace. 


![9](https://github.com/obi298/Azure-SIEM-Project/assets/90945162/38d0b709-fb87-4121-9306-a61f424f283e)

<br>
<br>
<br>


I went to the settings and enabled data collection for all events which allowed the virtual machine to capture data from attacks.


![12](https://github.com/obi298/Azure-SIEM-Project/assets/90945162/856033db-ad15-44cb-aabd-11514a9d131a)

<br>
<br>
<br>























