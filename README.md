# 🕵️‍♂️ CTF-DoubleTrouble-Machine  

A step-by-step walkthrough and resources for solving the **DoubleTrouble CTF machine (VulnHub)**.  
This repository is designed for **beginners in cybersecurity** and covers reconnaissance, enumeration, exploitation, steganography, credential extraction, privilege escalation, and root flag capture.  

---

## 📑 Repository Structure  

- README.md → Project overview (this file)
- Environment_Setup.md → Setup instructions (Kali + VM networking)
- Walkthrough.md → Full exploitation walkthrough
- Project_Report.pdf → Detailed report with screenshots
- references.md → Tools, resources & learning material
- commands/ → Key commands used during exploitation
- ├── nmap_scan.md
- ├── enumeration.md
- ├── reverse_shell_payload.md
- └── sqlmap_commands.md
- exploits/ → Exploit files & payloads
- ├── reverse_shell.md
- └── custom_payloads.md
- └── LICENSE → License (CC-BY 4.0)


---


## 🚀 Getting Started  

1. Import **DoubleTrouble VM** in VirtualBox/VMware.  
2. Set up your **attacking machine (Kali Linux)** in the same NAT network.  
3. Follow setup instructions: [Environment_Setup.md](./Environment_Setup.md).  
4. Begin exploitation using the step-by-step guide: [Walkthrough.md](./Walkthrough.md).  

---

## 📘 Documentation  

- **Walkthrough** → [Walkthrough.md](./Walkthrough.md)  
- **Project Report (with screenshots)** → [Project_Report.pdf](./Project_Report.pdf)  
- **Commands Reference** → [commands/](./commands/)  
- **Exploits Used** → [exploits/](./exploits/)  
- **Additional References** → [references.md](./references.md)  

---

## 🛠️ Tools Used  

- Nmap  
- Netdiscover  
- Dirb  
- Steghide / Stegcracker  
- SSH  
- Python (Privilege Escalation)  

---

## 🎯 Learning Objectives  

By following this project, you will:  
- Perform active and passive reconnaissance  
- Enumerate web applications for hidden files  
- Use steganography tools to extract hidden data  
- Crack credentials using wordlists  
- Gain a foothold in a vulnerable web application  
- Escalate privileges to root  

---

## 📜 License  

This project uses a **dual-license model**:  

- **Code (payloads, scripts, exploits, etc.)** → [MIT License](./LICENSE)  
- **Documentation (walkthrough, report, references, etc.)** → [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/)  

You are free to use, share, and adapt this work, but please provide proper attribution.


---

