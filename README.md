<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 22.04

<h2>High-Level Steps</h2>

- Create two virtual machines
- Observe ICMP traffic 
- Configure a firewall
- Observe SSH, DNS and RDP traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://imgur.com/yf8JpSC.png" height="80%" width="80%"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/3qYhoNQ.png" height="80%" width="80%"/>
</p>
<p>
First, we create two virtual machines (VMs) in the Azure portal. One VM uses a Windows 10 Pro image, while the other uses an Ubuntu (Linux) image. Each of the VMs are created with 2 vCPUs. During setup, we make sure that both VMs are attached to the same virtual network. We then use Remote Desktop (RDP) to access the Windows VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/2oKrPX9.jpg" height="80%" width="80%"/>
</p>
<p>
From within the Windows VM, we download and install Wireshark from https://www.wireshark.org. This tool will be used to observe network traffic. After installing Wireshark, we open the application and filter for ICMP traffic. ICMP is used to check connectivity between network devices.
</p>
<br />

<p>
<img src="https://i.imgur.com/SR5tqWa.jpg" height="80%" width="80%"/>
</p>
<p>
We then open PowerShell. We use the ping command to test the connectivity to the Linux VM, which is on the same network, using its private IP address. (The private IP address is found on the Azure portal under the VM’s network settings.)
</p>
<br />

<p>
<img src="https://i.imgur.com/sEdJMxa.jpg" height="80%" width="80%"/>
</p>
<p>
Next, we use the ping -t command to continuously ping the Linux VM. We observe the never-ending traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/I0SiQBb.jpg" height="80%" width="80%"/>
</p>
<p>
We then go back to the Azure portal, to the Linux VM. We navigate to its network settings and create an inbound port rule to deny ICMP traffic. This effectively creates a firewall, blocking the ICMP traffic that the Windows VM is pinging to the Linux VM. We then return to the Windows VM to check Wireshark. We see that the pings are no longer receiving replies from the Linux VM. In PowerShell, we see a repeated “Request Timed Out” message.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
