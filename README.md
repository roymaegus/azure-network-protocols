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

1. <h4>Create a Resource Group</h4>
   <img src="images/1 - Setup/1 - resourceGroups.PNG" alt="resourceGroups" width="50%" height="50%">
   <img src="images/1 - Setup/2 - reviewCreate.PNG" alt="reviewCreate" width="50%" height="50%">
<br />
<br />
<br />

3. **Create a Windows 10 Virtual Machine (VM)**
   - While creating the VM, select the previously created Resource Group.
   - Allow it to create a new Virtual Network (Vnet) and Subnet.
   <img src="images/1 - Setup/3- VmPage.PNG" alt="VmPage" width="50%" height="50%">
   <img src="images/1 - Setup/4 - vmCreateTop.PNG" alt="vmCreateTop" width="50%" height="50%">
   <img src="images/1 - Setup/5 - vmCreateBottom.PNG" alt="vmCreateBottom" width="50%" height="50%">
   <img src="images/1 - Setup/6 - skipDisk.PNG" alt="skipDisk" width="50%" height="50%">
   <img src="images/1 - Setup/7 - networking.PNG" alt="networking" width="50%" height="50%">
     <br />
     <br />
     <br />

4. **Create a Linux (Ubuntu) VM**
   - While creating the VM, select the previously created Resource Group and Vnet.
   <img src="images/1 - Setup/8 - createVM2.PNG" alt="createVM2" width="50%" height="50%">
   <img src="images/1 - Setup/9 - createVM2Bottom.PNG" alt="createVM2Bottom" width="50%" height="50%">
   <img src="images/1 - Setup/10 - skipDisk2.PNG" alt="skipDisk2" width="50%" height="50%">
   <img src="images/1 - Setup/11 - networking2.PNG" alt="networking2" width="50%" height="50%">
      <br />
      <br />
      <br />

<h4>Connect to your VM by remote desktop connection</h4>
<img src="images/1 - Setup/12 - remoteDesktop.PNG" alt="remoteDesktop" width="50%" height="50%">

<h4>Turn of all options</h4>
<img src="images/1 - Setup/13 - privacySettings.PNG" alt="privacySettings" width="50%" height="50%">



## Part 2 (Observe ICMP Traffic)

<h4>Search for Wireshark, download, and setup</h4>
<img src="images/1 - Setup/14 - wireSharkSearch.PNG" alt="wireSharkSearch" width="50%" height="50%">
<img src="images/1 - Setup/15 - downloadWireshark.PNG" alt="downloadWireshark" width="50%" height="50%">
<img src="images/1 - Setup/16 - wiresharkInstall.PNG" alt="wiresharkInstall" width="50%" height="50%">
<br />
<br />
<br />



3. **Open Wireshark and filter for ICMP traffic only**

<img src="images/2 - observation/17 - wireSharkHome.PNG" alt="wireSharkHome" width="50%" height="50%">
<img src="images/2 - observation/18 - randomDataCapture.PNG" alt="randomDataCapture" width="50%" height="50%">
<img src="images/2 - observation/19 - searchIcmp.PNG" alt="searchIcmp" width="50%" height="50%">


5. **Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM**
<img src="images/2 - observation/20 - privateIpAdressVm2.PNG" alt="privateIpAdressVm2" width="50%" height="50%">
   
7. **Observe ping requests and replies within Wireshark**
<img src="images/2 - observation/21 - openPowershell.PNG" alt="openPowershell" width="50%" height="50%">
<img src="images/2 - observation/22 - pingVM2.PNG" alt="pingVM2" width="50%" height="50%">
<img src="images/2 - observation/23 - clearData.PNG" alt="clearData" width="50%" height="50%">

10. **Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM**
<img src="images/2 - observation/24 - infinitePing.PNG" alt="infinitePing" width="50%" height="50%">
<img src="images/2 - observation/25 - infinitePingActive.PNG" alt="infinitePingActive" width="50%" height="50%">




11. **Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic**

   <img src="images/2 - observation/26 - NetworkSecurityGroups.PNG" alt="NetworkSecurityGroups" width="50%" height="50%">
<img src="images/2 - observation/27 - selectNSG.PNG" alt="selectNSG" width="50%" height="50%">
<img src="images/2 - observation/28 - inboundSecurity.PNG" alt="inboundSecurity" width="50%" height="50%">
<img src="images/2 - observation/29 - inboundSecurityRuleConfig.PNG" alt="inboundSecurityRuleConfig" width="50%" height="50%">


13. **Back in the Windows 10 VM, observe the ICMP traffic in Wireshark and the Command Line Ping activity**
<img src="images/2 - observation/30 - timeOut.PNG" alt="timeOut" width="50%" height="50%">
    
15. **Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using**
<img src="images/2 - observation/31 - allowPing.PNG" alt="allowPing" width="50%" height="50%">

    
17. **Back in the Windows 10 VM, observe the ICMP traffic in Wireshark and the Command Line Ping activity (should start working)**

<img src="images/2 - observation/32 - successfulPing.PNG" alt="successfulPing" width="50%" height="50%">

19. **Stop the ping activity**
<img src="images/2 - observation/33 - stopProcess.PNG" alt="stopProcess" width="50%" height="50%">
<br />
<br />
<br />

## Part 3 (Observe SSH Traffic)

3. **From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)**
<img src="images/2 - observation/34 - privateIPreminder.PNG" alt="privateIPreminder" width="50%" height="50%">
<img src="images/2 - observation/35 - sshCommand.PNG" alt="sshCommand" width="50%" height="50%">

1. **Back in Wireshark, filter for SSH traffic only. Observe SSH traffic.**
<img src="images/2 - observation/36 - accessVm2.PNG" alt="accessVm2" width="50%" height="50%">
   
7. **Exit the SSH connection by typing `exit` and pressing [Enter]**
<img src="images/2 - observation/37 - exitCommand.PNG" alt="exitCommand" width="50%" height="50%">

## Part 4 (Observe DHCP Traffic)

1. **Back in Wireshark, filter for DHCP traffic only. Observe the DHCP traffic appearing in Wireshark**
<img src="images/2 - observation/40 - dhcp.PNG" width="50%" height="50%">


## Part 5 (Observe DNS Traffic)

1. **Back in Wireshark, filter for DNS traffic only. Observe the DNS traffic being shown in Wireshark.**

<img src="images/2 - observation/38 - dnsObservation.PNG" alt="dnsObservation" width="50%" height="50%">

## Part 6 (Observe RDP Traffic)
**Back in Wireshark, filter for RDP traffic only. Observe the RDP traffic being shown in Wireshark.**
<img src="images/2 - observation/39 - rdp.PNG" alt="rdp" width="50%" height="50%">






