# 🛠 Environment Setup for CTF - DoubleTrouble Machine

This guide explains how to set up the lab environment used to solve the **DoubleTrouble CTF challenge** from VulnHub.  
It is written for **macOS users** running **Kali Linux on UTM**.

---

## 1️⃣ Host System
- **Operating System:** macOS  
- **Virtualization Tool:** [UTM](https://mac.getutm.app/) (free, open-source virtualization for macOS)  

---

## 2️⃣ Installing Kali Linux on UTM
1. Download **UTM** from the official site:  
   👉 [https://mac.getutm.app/](https://mac.getutm.app/)

2. Download the **Kali Linux ARM/ISO image**:  
   👉 [https://www.kali.org/get-kali/](https://www.kali.org/get-kali/)

3. Open UTM → click **Create a New Virtual Machine** → choose **Virtualize**.  
4. Select the downloaded **Kali ISO**.  
5. Allocate resources (recommended):  
   - **CPU:** 4 cores  
   - **RAM:** 4 GB (minimum 2 GB)  
   - **Disk:** 30 GB  
6. Finish setup and boot the VM.  
7. Install Kali Linux as usual and create a user account.  

---

## 3️⃣ Downloading the DoubleTrouble Machine
The target vulnerable machine is **DoubleTrouble**, available on VulnHub.

1. Download from VulnHub:  
   👉 [https://www.vulnhub.com/entry/doubletrouble-1,506/](https://www.vulnhub.com/entry/doubletrouble-1,506/)

2. Extract the archive — you’ll find `.ova` or `.vmdk` files.  
   (UTM can import **VMware/VirtualBox disk images**.)  

3. In UTM → create a **new Virtual Machine** → choose **Emulate** → import the disk file of DoubleTrouble.  

---

## 4️⃣ Networking Setup
To allow your **Kali attacker machine** to talk to the **DoubleTrouble victim machine**:
1. In UTM, set **both VMs** (Kali + DoubleTrouble) to **Shared Network (NAT)** or **Bridged Mode**.  
   - Shared (NAT) works fine, both machines get IPs in the same range.  
   - Bridged makes them appear on the same LAN as your macOS host.  

2. Boot both VMs.  
3. From Kali, run:  
   ```bash
   ip a
4.Scan the network to find DoubleTrouble's Ip
      namps -sn 192.168.1.0/24


##5️⃣ Tools Used
Ensure the following tools are installed on Kali:
>>nmap
>>gobuster
>>sqlmap
>>netcat
>>python3
>>gcc (for compiling exploits, if needed)
Install missing ones with:
sudo apt update && sudo apt install nmap gobuster sqlmap netcat gcc -y

✅ Setup Complete
At this point:
You have Kali Linux running on UTM (attacker machine).
You have the DoubleTrouble VulnHub VM running as target.
Both machines can communicate over the same virtual network.
You are ready to begin the challenge 🚀

