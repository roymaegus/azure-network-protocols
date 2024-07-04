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

# Azure Networking Lab

## Part 1 (Create our Resources)

1. **Create a Resource Group**
2. **Create a Windows 10 Virtual Machine (VM)**
   - While creating the VM, select the previously created Resource Group.
   - Allow it to create a new Virtual Network (Vnet) and Subnet.
3. **Create a Linux (Ubuntu) VM**
   - While creating the VM, select the previously created Resource Group and Vnet.
4. **Observe Your Virtual Network within Network Watcher**

## Part 2 (Observe ICMP Traffic)

1. **Use Remote Desktop to connect to your Windows 10 Virtual Machine**
2. **Within your Windows 10 Virtual Machine, Install Wireshark**
3. **Open Wireshark and filter for ICMP traffic only**
4. **Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM**
5. **Observe ping requests and replies within Wireshark**
6. **From the Windows 10 VM, open Command Line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in Wireshark**
7. **Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM**
8. **Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic**
9. **Back in the Windows 10 VM, observe the ICMP traffic in Wireshark and the Command Line Ping activity**
10. **Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using**
11. **Back in the Windows 10 VM, observe the ICMP traffic in Wireshark and the Command Line Ping activity (should start working)**
12. **Stop the ping activity**

## Part 3 (Observe SSH Traffic)

1. **Back in Wireshark, filter for SSH traffic only**
2. **From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)**
3. **Type commands (username, password, etc.) into the Linux SSH connection and observe SSH traffic spam in Wireshark**
4. **Exit the SSH connection by typing `exit` and pressing [Enter]**

## Part 4 (Observe DHCP Traffic)

1. **Back in Wireshark, filter for DHCP traffic only**
2. **From your Windows 10 VM, attempt to issue your VM a new IP address from the Command Line (`ipconfig /renew`)**
3. **Observe the DHCP traffic appearing in Wireshark**

## Part 5 (Observe DNS Traffic)

1. **Back in Wireshark, filter for DNS traffic only**
2. **From your Windows 10 VM within a Command Line, use `nslookup` to see what google.com and disney.com’s IP addresses are**
3. **Observe the DNS traffic being shown in Wireshark**

## Part 6 (Observe RDP Traffic)

1. **Back in Wireshark, filter for RDP traffic only (`tcp.port == 3389`)**
2. **Observe the immediate non-stop spam of traffic. Why do you think it’s non-stop spamming vs. only showing traffic when you do an activity?**
   - **Answer:** Because the RDP protocol is constantly showing you a live stream from one computer to another, therefore traffic is always being transmitted.

## Lab Cleanup (DON’T FORGET THIS)

1. **Close your Remote Desktop connection**
2. **Delete the Resource Group(s) created at the beginning of this lab**
3. **Verify Resource Group Deletion**



