# Lab Write‑ups Series  
  
## Overview  
This series of lab write‑ups documents hands‑on exercises in Cisco networking and Windows Server configuration. The labs demonstrate how to configure basic network devices, secure remote access, manage server roles, and implement network services. They are intended for educational purposes and to reinforce foundational networking and system administration skills.  
  
## Cisco Labs  
These labs focus on configuring Cisco routers and switches. Key tasks include ([itexamanswers.net](https://itexamanswers.net/lab-11-5-1-basic-cisco-device-configuration-answers.html#:~:text=Scenario%20%20Task%201%3A%20Configure,Step%206%3A%20Configure%20the%20virtual)):  
- Setting global configuration parameters (hostname, banners, and securing privileged EXEC mode with passwords).  
- Configuring user and console access, including VTY line passwords and enabling password encryption.  
- Assigning IP addresses to router interfaces, enabling interfaces, and verifying connectivity.  
- Saving the running configuration to non‑volatile memory (NVRAM).  
- Configuring basic switch settings and VLANs.  
  
### Example Cisco Configuration  
```plaintext  
! Set router hostname and secure privileged mode  
Router> enable  
Router# configure terminal  
Router(config)# hostname LabRouter  
Router(config)# enable secret S3cur3P@ss  
! Configure console and VTY line passwords  
Router(config)# line console 0  
Router(config-line)# password c0ns0le  
Router(config-line)# login  
Router(config)# line vty 0 4  
Router(config-line)# password vtypass  
Router(config-line)# login  
! Configure interface GigabitEthernet0/0 with IP address  
Router(config)# interface GigabitEthernet0/0  
Router(config-if)# ip address 192.168.1.1 255.255.255.0  
Router(config-if)# no shutdown  
! Save configuration  
Router# copy running-config startup-config  
```  
The comments above (prefaced with `!`) describe each step. In a real network, you would also configure routing protocols and security features.  
  
## Windows Server Labs  
The Windows labs involve configuring server roles and services on a Windows Server virtual machine. Tasks may include:  
- Installing roles such as Active Directory Domain Services (AD DS), DNS, DHCP, or Web Server (IIS).  
- Promoting a server to a domain controller and creating user and group accounts.  
- Setting up group policies to enforce password complexity or configure desktop settings.  
- Configuring network settings, NIC teaming, and firewall rules.  
- Managing shared folders and NTFS permissions.  
  
### Example PowerShell Commands  
```powershell  
# Install Active Directory Domain Services role  
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools  
  
# Promote the server to a new forest (replace domain name with your own)  
Install-ADDSForest -DomainName "corp.example.local" -SafeModeAdministratorPassword (Read-Host -AsSecureString "Enter DSRM password")  
  
# Create a new user  
New-ADUser -Name "Alice Johnson" -SamAccountName "alice.johnson" -UserPrincipalName "alice.johnson@corp.example.local" -AccountPassword (Read-Host -AsSecureString "Enter user password") -Enabled $true  
  
# Create a new security group and add the user  
New-ADGroup -Name "IT Support" -GroupScope Global -PassThru | Add-ADGroupMember -Members "alice.johnson"  
```  
Each command includes comments describing its purpose. You can adapt these scripts to automate repetitive tasks when configuring Windows servers.  
  
## Real‑World Scenario  
Imagine preparing for a network administrator role at a mid‑sized company. You need to configure a new branch office router, secure remote access, and set up a Windows Server domain for user authentication. These labs simulate those tasks, giving you confidence to perform them in a production environment.  
  
## Fun Fact  
Cisco’s first router, released in 1986, was built in a living room by Stanford University staff members Len Bosack and Sandy Lerner. Today, Cisco equipment forms the backbone of many enterprise networks, and mastering its configuration is a valuable skill.  
  
## Future Directions  
Future lab write‑ups could explore advanced topics like:  
- Implementing dynamic routing protocols (e.g., OSPF, EIGRP, or BGP).  
- Configuring Quality of Service (QoS) to prioritize voice and video traffic.  
- Deploying high‑availability features such as HSRP or VRRP.  
- Automating network and server configuration using Ansible, PowerShell DSC, or Python scripts.  
- Exploring cloud networking services in platforms like AWS or Azure.
