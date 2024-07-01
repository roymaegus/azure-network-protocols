Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups.
Environments and Technologies Used
Microsoft Azure (Virtual Machines/Compute)
Remote Desktop
Various Command-Line Tools
Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
Wireshark (Protocol Analyzer)
Operating Systems Used
Windows 10 (21H2)
Ubuntu Server 20.04
High-Level Steps
Create Resource Groups and Virtual Machines
Install & Run Wireshark
Observe ICMP Traffic
Observe SSH Traffic
Observe DHCP Traffic
Observe RDP Traffic
Actions and Observations
Create Resource Groups and Virtual Machines
Disk Sanitization Steps

In Microsoft Azure, create a resource group and two virtual machines. Creating the VM will also allow you to create a new virtual network aka (Vnet). Create a Windows client virtual machine and an Linux (Ubuntu) server. Use the same Vnet that was created for your Windows VM.


Install and Run Wireshark
Disk Sanitization Steps

Go into your Windows Virtual Machine and open an internet browser and search "download Wireshark" and download it from the actual website. Wireshark is a network protocol analyzer. It is used to troubleshoot networks, analysis, software & protocol development, and education. It is the most widely used network analyzer.


Disk Sanitization Steps

On the website, click on Windows Installer to download-->Click Open File from the Downloads window on your browser-->Click next on the setup dialog box and advance next to install all of the prerequisite programs required to install Wireshark.


Disk Sanitization Steps

Open Wireshark and click on the blue fin icon located right under the file menu. Once you click on that icon, Wireshark will start analyzing all network traffic on the virtual machine.


Observe ICMP Traffic
Disk Sanitization Steps

Use the Remote Destkop Windows 10 Virtual Machine. Use Wireshark to filter traffic for ICMP by typing it in the filter bar and click on the blue arrow button to the right to start the filter.


Disk Sanitization Steps

Retrieve the private IP address of the Linux (Ubuntu) virtual machine and attepmt to ping it in the Windows 10 virtual machine.


Disk Sanitization Steps

From the Windows 10 virtual machine open Powershell and attempt to ping the private IP address of VM 2 server and observe the requests and replies within Wireshark.


Disk Sanitization Steps

From the Windows 10 virtual machine, open PowerShell and attempt to ping www.google.com and observe the traffic in Wireshark.

From the PowerShell, you can see the packets of data sent and the statics at the bottom.

From Wireshark, you can see the packets of data replied through google.com and the data being sent.


Disk Sanitization Steps

From the Windows 10 virtual machine. Send a non-stop ping request in Windows Powershell buy typing ping -t www.google.com.

It will receive non-stop packet requests until you cancel it. To cancel the ping request go to PowerShell and hit ctrl+C.


Disk Sanitization Steps

In the Microsoft Azure portal open Network Security Group on your VM2 to initiate a perpetual/non-stop ping from your Windows 10 virtual machine to your Ubuntu VM.


Disk Sanitization Steps

In your Windows 10 virtual machine, observe the ICMP traffic in WireShark and the command line Ping activity.


Disk Sanitization Steps

In Microsoft Azure network security group settings. Select your deny ICMP settings and allow ICMP traffic to resume.


Disk Sanitization Steps

In your Windows 10 virtual machine, ping your Ubuntu server VM2 private IP address and observe the packets of data resume.


Observe SSH Traffic
Disk Sanitization Steps

In your Windows 10 virtual machine connect to your Unbuntu (VM2) virtual machine using SSH via Powershell. Use the command SSH your VM2 username@VM2 private address and hit enter. Type your password and hit enter.


Disk Sanitization Steps

From your Window 10 virtual machine (VM1) type in commands (ld, uname -a, pwd, and ls lasth) and observe the output in PowerShell and data packets in WireShark.

To logout out of the server, type "exit" in the command line in PowerShell and hit enter.


Observe DHCP Traffic
Disk Sanitization Steps

From your Windows 10 virtual machine. Filter DHCP traffic in the search bar on WireShark. On PowerShell renew your IP address lease by typing in the command line ipconfig /renew. *Your virtual machine will get assigned a new IP address. Observe the DHCP traffic in WireShark echo request.

*Note your VM may disconnect when getting assigned a new IP address.


Observe DNS Traffic
Disk Sanitization Steps

From Windows 10 virtual machine. Filter out DNS network traffic in Wireshark by typing DNS in the search bar. From Windows PowerShell give command line "nslookup www.google.com" Observe Google's IP address and DNS returned in PowerShell. Observe the IP address and DNS returned in the data packets in WireShark


Observe RDP Traffic
Disk Sanitization Steps

From your Windows 10 virtual machine. Go to WireShark and type RDP in the search bar to filter only RDP traffic. Click on the blue arrow to the right to activate the filter. Observe the network traffic in WireShark.
