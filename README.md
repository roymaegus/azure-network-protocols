# Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines

In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups.

## Environments and Technologies Used
- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

## Operating Systems Used
- Windows 10 (21H2)
- Ubuntu Server 20.04

## High-Level Steps
1. Create Resource Groups and Virtual Machines
2. Install & Run Wireshark
3. Observe ICMP Traffic
4. Observe SSH Traffic
5. Observe DHCP Traffic
6. Observe RDP Traffic

## Actions and Observations

### Create Resource Groups and Virtual Machines
1. In Microsoft Azure, create a resource group and two virtual machines. Creating the VM will also allow you to create a new virtual network (Vnet). Create a Windows client virtual machine and a Linux (Ubuntu) server. Use the same Vnet that was created for your Windows VM.

### Install and Run Wireshark
1. Go into your Windows Virtual Machine and open an internet browser. Search "download Wireshark" and download it from the official website. Wireshark is a network protocol analyzer used for troubleshooting networks, analysis, software & protocol development, and education. It is the most widely used network analyzer.
2. On the website, click on Windows Installer to download. Click Open File from the Downloads window on your browser. Click next on the setup dialog box and advance next to install all of the prerequisite programs required to install Wireshark.
3. Open Wireshark and click on the blue fin icon located right under the file menu. Once you click on that icon, Wireshark will start analyzing all network traffic on the virtual machine.

### Observe ICMP Traffic
1. Use the Remote Desktop Windows 10 Virtual Machine. Use Wireshark to filter traffic for ICMP by typing it in the filter bar and clicking on the blue arrow button to the right to start the filter.
2. Retrieve the private IP address of the Linux (Ubuntu) virtual machine and attempt to ping it in the Windows 10 virtual machine.
3. From the Windows 10 virtual machine, open PowerShell and attempt to ping the private IP address of the VM2 server and observe the requests and replies within Wireshark.
4. From the Windows 10 virtual machine, open PowerShell and attempt to ping www.google.com and observe the traffic in Wireshark.
   - From PowerShell, you can see the packets of data sent and the statistics at the bottom.
   - From Wireshark, you can see the packets of data replied through google.com and the data being sent.
5. From the Windows 10 virtual machine, send a non-stop ping request in Windows PowerShell by typing `ping -t www.google.com`.
   - It will receive non-stop packet requests until you cancel it. To cancel the ping request, go to PowerShell and hit Ctrl+C.
6. In the Microsoft Azure portal, open Network Security Group on your VM2 to initiate a perpetual/non-stop ping from your Windows 10 virtual machine to your Ubuntu VM.
7. In your Windows 10 virtual machine, observe the ICMP traffic in Wireshark and the command line Ping activity.
8. In Microsoft Azure network security group settings, select your deny ICMP settings and allow ICMP traffic to resume.
9. In your Windows 10 virtual machine, ping your Ubuntu server VM2 private IP address and observe the packets of data resume.

### Observe SSH Traffic
1. In your Windows 10 virtual machine, connect to your Ubuntu (VM2) virtual machine using SSH via PowerShell. Use the command `ssh [your VM2 username]@[VM2 private address]` and hit enter. Type your password and hit enter.
2. From your Windows 10 virtual machine (VM1), type in commands (`ls`, `uname -a`, `pwd`, and `ls -lah`) and observe the output in PowerShell and data packets in Wireshark.
   - To logout of the server, type `exit` in the command line in PowerShell and hit enter.

### Observe DHCP Traffic
1. From your Windows 10 virtual machine, filter DHCP traffic in the search bar on Wireshark. On PowerShell, renew your IP address lease by typing in the command line `ipconfig /renew`.
   - Your virtual machine will get assigned a new IP address. Observe the DHCP traffic in Wireshark echo request.
   - *Note: Your VM may disconnect when getting assigned a new IP address.*

### Observe DNS Traffic
1. From the Windows 10 virtual machine, filter out DNS network traffic in Wireshark by typing DNS in the search bar. From Windows PowerShell, give the command line `nslookup www.google.com`. Observe Google's IP address and DNS returned in PowerShell. Observe the IP address and DNS returned in the data packets in Wireshark.

### Observe RDP Traffic
1. From your Windows 10 virtual machine, go to Wireshark and type RDP in the search bar to filter only RDP traffic. Click on the blue arrow to the right to activate the filter. Observe the network traffic in Wireshark.
