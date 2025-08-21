# 🔍 Nmap Scan Results

This file documents the Nmap scan results for the **DoubleTrouble CTF machine**.

---

## Command Used
```bash
nmap -p- -n -vvv -sCV 10.0.2.4
```
- `-p-` → Scan all ports (1–65535)
- `-n` → Do not resolve DNS
- `-vvv` → Very verbose output (faster discovery)
- `-sCV` → Default scripts + service/version detection
___  
## Scan Results
```bash
22/tcp   open  ssh     OpenSSH 7.6p1 Ubuntu 4 (Ubuntu Linux; protocol 2.0)
80/tcp   open  http    Apache httpd 2.4.29 ((Ubuntu))
```
___  
## Observations
- **Port 22 (SSH)** is open → later stage access possible via credentials.
- **Port 80 (HTTP)** is open → hosts the qdPM login page, primary attack surface.