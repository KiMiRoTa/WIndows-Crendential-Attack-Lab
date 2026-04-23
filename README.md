# WIndows-Crendential-Attack-Lab

## Overview
This repository is my university project about simulating credential dumping and privilege escalation in a Windows Active Directory environment

The attack does NOT rely on software vulnerabilities, but instead exploits:
- Weak password
- Cached credentials
- Unsafe administrator behavior

---

## Lab Environment
- Windows Server (Domain Controller) 
- Windows 10 (Client)
- Kali Linux (Attacker)
- VirtualBox

---

## Tools Used
- Nmap
- Kerbrute
- CrackMapExec
- THC Hydra
- Mimikatz

---

## Attack Flow
### 1. Reconnaissance (Nmap)
The attacker scans the Domain Controller to identify open ports and services such as Kerberos, LDAP, SMB, and DNS.
![Nmap Scan](./Images/NmapScan.png)
![Nmap Scan](./Images/NmapPortScan.png)
![Nmap Scan](./Images/NmapPortScan2.png)

### 2. Username Enumeration (Kerbrute)
Kerbrute is used to identify valid  usernames in the domain without requiring passwords.
![Kerbrute](./Images/Kerbrute.png)

### 3. SMB Enumeration (CrackMapExec)
CrackMapExec is used to gathe information from the Domain Controller via SMB services.
![CrackMapExec](./Images/CrackMapExec.png)

### 4. Password Brute Force (Hydra)
A brute-force attack is performed against the RDP service using the valid username.
![THC Hydra](./Images/THCHydra.png)

### 5. Initial Access (RDP Login)
Using the valid credentials, the attacker logs into the Windows 10 workstation via RDP.
![RDP](./Images/RDPfromKali.png)

### 6. privilege Escalation
Since the Domain Administrator previously logged into the system, credentials are cached and can be extracted.
![Escalation](./Images/Escalation1.png)
![Escalation](./Images/Escalation2.png)

---

Result
Full domain compromise achieved by:
- Reusing cached Domain Admin credentials
- Adding attacker-controlled user into Domain Admin Group

---

## Security Lessons
- Enforce strong password policies
- Avoid admin login on user machines
- Restrict RDP access

--- 

## Full report
See the full documentation here:
--> [ProjectWindowsActiveDirectoryPentest](./ProjectWindowsActiveDirectoryPentest.pdf) <--

---

Author 
- KiMiRoTa
