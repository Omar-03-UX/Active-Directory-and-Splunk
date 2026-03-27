# Active-Directory-and-Splunk
<p align="center">
 <br/>
 <br/>
<img src="https://i.imgur.com/YT6ivIv.png" height="80%" width="80%" alt="Protocol"/>

In this lab I setup an Active Directory home lab that became a treat detection lab that was intended to focus on tracking traces. The primary objectives of this lab focused on Telemetry Collection, Log Forwarding, Advesary simulation, Alert correlation and Incident Investigation. 

<br />
<h2> Utilities Used</h2>

- <b>Windows Server</b>
- <b>Splunk(Ubuntu)</b> 
 <b>Splunk(Ubuntu)</b> 
 <b>Windows 10</b> 
 <b>Kali</b> 

These are the (recommended Specs for the lab) 

- CPU: 4+ cores (8+ best)
- RAM: 16GB minimum (32GB is smooth)
- Storage: 150GB free (SSD best)

- **Splunk (Ubuntu):** 4 vCPU, 8GB RAM, 60GB disk (centralized SIEM and log analysis)
- **Windows 10:  (**Endpoint is for telemetry collection and attack stimulation)
- **Windows Server 2022:** 2–4 vCPU, 6–8GB RAM, 60GB disk (RDP enabled here)
- **Kali:** 2 vCPU, 2–4GB RAM, 30GB disk (Red team behavior for stimulating adversary behavior)

**Step 1**

Download the relevant ISO for:  

- Ubuntu Server
- Windows Server 2022
- Windows 10 (or 11)
- Kali Linux

**Step 2: VMware Networking**

- Use NAT to enable devices to seamlessly communicate with each other.

**Step 3**

- I created an Ubuntu VM, by going to VMware → **Create New VM**
- Ubuntu ISO is selected, for etc Ubuntu 64-bit ISO.
- Once the instructions are followed by download, make sure to update Ubuntu, and upgrade it using the following command.
- **“sudo apt update &&sudo apt upgrade -y”**
- I used the command  **ip  a  to check the existing configuration of Ubuntu.**
- By using nano, and entering this command in the terminal - **Sudo/etc/netplan/50**, This will allow you to perform static types of configuration, also configuring default gateway and a manual IP assigned.

**Step 4:  Set up Active Directory using (Windows Server 2022)** 

- Promoted the server to a Domain Controller
- Configured DNS, created test users
- Joined Windows 10 endpoint to the domain

- **Step 5:** 

- Installed Splunk Enterprise
- Configured Inputs to receive logs on port 9997
- Setup the web interface for log search and alerting

- **Step 6:** 

- Configured Windows 10 Endpoint
- Joined the Domain
- Installed **Splunk Universal Forwarder**
- Deployed **Sysmon** for the deep process/network telemetry


  **Phase 2: Attack Simulation Triggering Real Telemetry**

Step 1: I used Kali Linux to run attacks and Atomic Red Team on Windows to replicate known TTPs.

- We install crowbar into Kali Linux using the command ***Sudo apt-get install -y crowbar***
- Before installing crowbar update Kali using the command - (***Sudo apt-get update && sudo  apt-get upgrade -y***
- Head -n 20 rockyou.txt shows you the first 20 passwords
- output password to password.txt using >

Step 2:  Enable Remote Desktop Connection from the client machine

Commands I used after downloading Splunk Enterprise on Ubuntu. 

- **cd /tmp** for moving Splunk into a tmp folder
- **sudo apt - fix-broken install -y**
- **Sudo /opt/splunk/bin/splunk start**
- **sudo /opt/splunk/bin/splunk enable boot-start -user splunk -** for allowing Splunk to start once you reboot the machine.

Step 3: Crowbar: I used the command crowbar -b rdp -u bsmith -C password.txt -s 192.168.10.116 

This is used to target the target machine.  Important to make sure DNS is pointed to DC for the connectivity of RDP service to work. 

The commands I used were as follows: 

*cat /etc/resolve.conf (for checking DNS IP)*  

*Echo "nameserver “Nameserver" | sudo tee /etc/resolv.conf  (for changing the current DNS to follow the domain controller)*

step 4: Atomic red team installation, add an exclusion for the entire C drive as microsoft defender will detect atomic red team. 

The selected tactic is invoked here. 


<br />
<h2> Utilities Used</h2>
- <b>VM WORKSTATION</b> 

<p align="center">
 <br/>
<br /> <img src="https://i.imgur.com/9UDdSPS.png" height="80%" width="80%" alt="Protocol"/>
<br />
<img src="https://i.imgur.com/ceAHwQ3.png" height="80%" width="80%" alt="Protocol"/>
<br />
<img src="https://i.imgur.com/7ewAlHk.png" height="80%" width="80%" alt="Source"/>
<br /> 
<img src="https://i.imgur.com/IovcBTy.png" height="80%" width="80%" alt="Source"/>
<br />
<img src="https://i.imgur.cm/IovcBTy.png" height="80%" width="80%" alt="Source"/>
<br />
<img src="https://i.imgur.com/aOMAxDQ.png" height="80%" width="80%" alt="Source"/>
<br />
<img src="https://i.imgur.com/s3JESLI.png" height="80%" width="80%" alt="Source"/>
<br />
<img src="https://i.imgur.com/7hLdbcs.png" height="80%" width="80%" alt="Source"/>
<br />
<img src="https://i.imgur.com/ofP5GkM.png" height="80%" width="80%" alt="Source"/>
<br />
<img src="https://i.imgur.com/PQwHMYo.png" height="80%" width="80%" alt="Source"/>
<br />
<img src="https://i.imgur.com/6bDpsqo.png" height="80%" width="80%" alt="Source"/>
<br />
