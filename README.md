<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


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
<img src="https://i.imgur.com/r6f8x3v.jpg" height="80%" width="80%"/>
</p>
<p>
Afterward, we go back into the Linux VM on the Azure portal to delete the inbound port rule. This allows the ICMP traffic to resume unhindered between the two VMs. To stop the continuous pinging, we press Ctrl + C in PowerShell.
</p>
<br />

<p>
<img src="https://i.imgur.com/2q3HOsg.jpg" height="80%" width="80%"/>
</p>
<img src="https://i.imgur.com/ylUbqPv.jpg" height="80%" width="80%"/>
<p>
Next, we filter SSH traffic using Wireshark. We open the command prompt on the Windows VM and establish an SSH connection to the Linux VM using the command: ssh mamanatlab@10.0.0.5. When the command is executed, Wireshark displays the SSH traffic, allowing us to observe and analyze it in real time. When we’re done, we type “exit” to end the Linux SSH connection.
</p>
<br />

<p>
<img src="https://i.imgur.com/t4JDeaa.jpg" height="80%" width="80%"/>
</p>
<p>
Then we filter DNS traffic in Wireshark. We start by setting Wireshark to display only DNS traffic. To generate DNS activity, we use the command nslookup www.amazon.com. This queries the DNS server for Amazon’s IP address.
</p>
<br />

<p>
<img src="https://i.imgur.com/f6G4p9o.jpg" height="80%" width="80%"/>
</p>
<p>
Lastly, we filter for RDP traffic in Wireshark. The RDP traffic will appear continuously since we are using Remote Desktop Protocol to connect to our virtual machine. As such, we are provided with ample date for analysis.
</p>
<br />



