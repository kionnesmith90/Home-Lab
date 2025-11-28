# Home-Lab

## Home Lab Overview:
In this project, we will explore how to set up a Cybersecurity Home Lab on our laptop/PC.
This project has been heavily inspired by the following Home Lab guides:

https://infosecwriteups.com/building-a-virtual-security-home-lab-part-1-network-topology-a373f93e342b

## Layers to the Lab:
- pfSense (Gateway & Firewall)
- Kali Linux (Management VM)
- Active Directory Lab (Domain Controller & 2 Clients)
- Malware Analysis Lab (Windows & Linux)
- Security VMs (DFIR & SIEM)
- Cyber Range (Vulnerable VMs for CTF practice)

<img width="362" height="581" alt="image" src="https://github.com/user-attachments/assets/0bf38ad8-bd76-48ca-bfb9-7876f2079ab3" />

## Part 1:
### Creating VM (pfsense) As Firewall
<img width="397" height="465" alt="image" src="https://github.com/user-attachments/assets/5187a2ef-395a-41aa-80ad-185abbc84e03" />
 
### Adding the New pfSense into a group
<img width="397" height="397" alt="image" src="https://github.com/user-attachments/assets/0659a2fb-1df6-4655-8094-d5c6adad2efc" />

### Renamed group to firewall
<img width="397" height="172" alt="image" src="https://github.com/user-attachments/assets/e24830c9-74d3-40b0-9199-c14d31f9ce6a" />

### pfSense VM Configuration:
- Changed the order of the boot order to HDD then Optical next and ensured that the floppy is unchecked.
- Disabling audio / Usb as well since we wont need it
<img width="397" height="341" alt="image" src="https://github.com/user-attachments/assets/57c09c60-68c6-4db4-abd2-7dd15043d640" />

### Network Configuration:
- Configuring the network and creating LANs
<img width="397" height="473" alt="image" src="https://github.com/user-attachments/assets/de094fdf-ebba-439f-a4d4-9dd0d20a33e9" />
<img width="397" height="486" alt="image" src="https://github.com/user-attachments/assets/ec13ca17-e156-4699-a95c-e8cb39b4197d" />
<img width="397" height="458" alt="image" src="https://github.com/user-attachments/assets/0f876866-556b-4b29-84be-7c7afc669724" />
<img width="397" height="432" alt="image" src="https://github.com/user-attachments/assets/5fb0542e-6935-47b4-be96-5494b58477df" />
 
### pfSense Configuration:
- Changing the IP addresses on LAN OPT1 & OPT2
- Also, completing the onboarding of the interfaces in pfSense
<img width="397" height="456" alt="image" src="https://github.com/user-attachments/assets/3fa30704-9fc9-45c4-9b69-2b15bafa2d15" />
 
### Kali Linux VM creation:
- This is created to act as a management group and also to run ivestigations
<img width="397" height="258" alt="image" src="https://github.com/user-attachments/assets/cfa2e61a-6fb0-4c04-a955-2bc299800984" />
 
### System Configuration & Network Configuration
<img width="397" height="480" alt="image" src="https://github.com/user-attachments/assets/c98cbe6e-5a05-4e17-877d-eb637f682634" />
<img width="397" height="300" alt="image" src="https://github.com/user-attachments/assets/ea0a569e-3e31-467e-af50-5050e24e90e1" />
<img width="397" height="470" alt="image" src="https://github.com/user-attachments/assets/647e9d5f-1f32-4c2b-b81a-4963239b1af2" />
 
#### Post-Installation Configuration 
- Ran the command: ip a. We can see that the Kali VM has been assigned an IP address from the LAN network range.
<img width="379" height="311" alt="image" src="https://github.com/user-attachments/assets/09375d1e-79d3-4bd9-ba5c-9c02a0518a5b" />

### Web Portal Setup
- Navigating to one of our LAN / subnets through the web browser
<img width="397" height="601" alt="image" src="https://github.com/user-attachments/assets/98c06d3f-e9f5-4dc1-a1cd-dfa4901bd728" />
<img width="397" height="286" alt="image" src="https://github.com/user-attachments/assets/d2b14b11-0f77-4a96-b1fa-895ef39e8f79" />
 
- From the navigation bar select Interfaces -> OPT2
- In the Description field enter AD_LAB
 
<img width="397" height="277" alt="image" src="https://github.com/user-attachments/assets/1a5f1053-74c5-4094-a217-6024c0702bfc" />
 
#### Kali Linux Static IP Assignment
- Click on the highlighted + icon to assign a static IP to Kali Linux.
<img width="397" height="185" alt="image" src="https://github.com/user-attachments/assets/0830235c-dc4e-4ee8-ab53-e63a0931aaae" />

#### Refresh Kali Linux IP Address 
<img width="397" height="160" alt="image" src="https://github.com/user-attachments/assets/bf1d3bad-9f79-4125-9767-ee88bf5fc5d2" />

- We want the VM to release the current IP address and use the static IP that was reserved. This can be achieved using the following command:

- " sudo ip l set eth0 down && sudo ip l set eth0 up "

<img width="397" height="157" alt="image" src="https://github.com/user-attachments/assets/53f99181-0ada-4666-a141-b7e2f2769958" />

## pfSense Firewall Configuration

- Changing the following options:
- Action: Block
- Address Family: Ipv4+IPv6
- Protocol: Any
- Source: LAN subnets
- Destination: WAN subnets
- Description: Block access to services on WAN interface

<img width="397" height="472" alt="image" src="https://github.com/user-attachments/assets/5023044d-426f-43bd-88db-8e3c19867a77" />

### CYBER_RANGE Rules
- Before creating the rules for CYBER_RANGE we need to create a Alias.

Entered the following details:
- Name: RFC1918
- Description: Private IPv4 Address Space
- Type: Network(s)
- Network 1: 10.0.0.0/8
- Network 2: 172.16.0.0/12
- Network 3: 192.168.0.0/16
- Network 4: 169.254.0.0/16
- Network 5: 127.0.0.0/8

<img width="397" height="193" alt="image" src="https://github.com/user-attachments/assets/1bb248fa-dc2d-479f-8688-8c611a0019c9" />
 
### ADDING RULES TO CYBER_RANGE
- Address Family: IPv4+IPv6
- Protocol: Any
- Source: CYBER_RANGE subnets
- Destination: CYBER_RANGE address
- Description: Allow traffic to all devices on the CYBER_RANGE network
<img width="397" height="467" alt="image" src="https://github.com/user-attachments/assets/82d92b5a-7056-47a0-b4c5-4e805e58e311" />

#### Then created another rule:
- Protocol: Any
- Source: CYBER_RANGE subnets
- Destination: Address or Alias - 10.0.0.2
- Description: Allow traffic to Kali Linux VM

- Protocol: Any
- Source: CYBER_RANGE subnets
- Destination: Address or Alias - RFC1918 (Select Invert match)
- Description: Allow to any non-private IPv4 Address

- Action: Block
- Address Family: IPv4+IPv6
- Protocol: Any
- Source: CYBER_RANGE subnets
- Description: Block access to everything

<img width="397" height="327" alt="image" src="https://github.com/user-attachments/assets/6ccba114-b597-43c8-ab8d-59f2bf4bbdcb" />

