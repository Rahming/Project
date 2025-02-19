# So You Want to be a SOC Analyst
Link to the Project (https://blog.ecapuano.com/p/so-you-want-to-be-a-soc-analyst-intro)

## Objective
1. Setting up and managing a SOC environment.

2. Understanding how to detect, analyze, and respond to cyber threats.

3. Developing and tuning detection rules to identify malicious activities.

4. Learning how to implement threat mitigation strategies.

### Skills Learned

1.SOC Environment setup

2.Threat Dectection and Analysis

3.Rule Creation and Tuning

4.Incident Response and Mitigation

5.YARA scanning

6.Threat Intelligence and reporting

### Tools Used
1. Virtualization Software

2. Security Information and Event Management (SIEM) tools

3. Network Monitoring 

4. YARA

5. Kali Linux 

## Steps
# PART 1. 
The first step was to set up the virtual environment. For this project "VMware Workstation Pro" by Broadcom was the software used. 

Ubuntu Server 22.04.1 ISO was the version used because this version comes pre Installed with necessary packages to do this project.

The VM Workstation created had the following specs: 14GB Disk size, 2 CPU cores, and 2GB RAM.

After downloading and setting everything up, I encountered my first error. I had to make sure DNS and outbound pings are working.


## This is what it is supposed to look like


![Screenshot (3)](https://github.com/user-attachments/assets/2565610e-979d-446e-99b8-ef3b094732ad)


## This is what I got

![Screenshot (2)](https://github.com/user-attachments/assets/ec614aca-52e4-477e-9de6-83bddb195d7c)

Seeing the response I noticed that I did not add a name server. To resolve the issue I entered the following command: 


sudo nano /etc/resolv.conf 


This allowed me to add a name server. I entered in 8.8.8.8 because it refers to one of Googles public DNS servers.


![Screenshot (4)](https://github.com/user-attachments/assets/87f0b3ad-9bb7-47e8-8401-b5bd41c820c1)

it started to work after the change.

![Screenshot (5)](https://github.com/user-attachments/assets/fe241b07-600a-4d1a-9b74-11c7776b2dec)


This Unbuntu VM will act as an attacker. Now that everything is working, I started to set up the windows VM. 

The link for the windows VM was not working so I  settled for a windows 11 x64 VM. After setting everything up, I disabled windows defender.

![Screenshot (6)](https://github.com/user-attachments/assets/2da84f22-48ab-48e5-a58a-17c487c0eb7b)

Ran the command to permanently disable defender via registry: 

REG ADD "hklm\software\policies\microsoft\windows defender" /v DisableAntiSpyware /t REG_DWORD /d 1 /f 

![Screenshot (7)](https://github.com/user-attachments/assets/1193917a-3529-4f9f-92f0-ba7eb4135684)

Now in safe mode, change the 7 sevices from 3 to 4.

![Screenshot (8)](https://github.com/user-attachments/assets/98048272-b3fc-4804-a79e-123731245f17)

Exit safe mode and it should be defender free.

Next I had to Install Sysmon which is a analyst tool.

 ![Screenshot (9)](https://github.com/user-attachments/assets/048b935d-f6b8-402c-bcb3-13300d366bb1)


LimaCharlie EDR is next to download. I had a little hiccup here. I had to put Lc_sensor.exe before the command line. I also had to enter DIR command to make sure lc_sensor.exe was there. It'll give an error message if lc_sensor.exe is entered in before the downloaded executable.

![Screenshot (10)](https://github.com/user-attachments/assets/9b6e2b30-f9ef-49d2-ab4a-b85c0c0ae42d)

Next was back to the attack system. I had to download sliver Linux server binary and create a directory for the future steps.


![Screenshot (11)](https://github.com/user-attachments/assets/d40b7860-deff-4c72-8783-067de2f4313d)

## Part 2 
