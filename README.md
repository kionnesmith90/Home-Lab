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




