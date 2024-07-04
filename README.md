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

<h5>Generate users to work with</h5>
<img src="images/47 - psIseAdmin.PNG" alt="psIseAdmin" width="50%" height="50%">
<img src="images/48 - addScript.PNG" alt="addScript" width="50%" height="50%">
<img src="images/49 - createRandomUsers.PNG" alt="createRandomUsers" width="50%" height="50%">
<img src="images/50 - employeeGenResult.PNG" alt="employeeGenResult" width="50%" height="50%">
<img src="images/51 - randomUserLogin.PNG" alt="randomUserLogin" width="50%" height="50%">
<img src="images/52 - loginScreen.PNG" alt="loginScreen" width="50%" height="50%">
<img src="images/53 - loginFail.PNG" alt="loginFail" width="50%" height="50%">
<img src="images/54 - accountUnlock.PNG" alt="accountUnlock" width="50%" height="50%">
<img src="images/55 - passwordReset.PNG" alt="passwordReset" width="50%" height="50%">
</br>
