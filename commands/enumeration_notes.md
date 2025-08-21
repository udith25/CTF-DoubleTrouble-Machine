# 📝 Enumeration Notes

This file contains enumeration notes and findings for the **DoubleTrouble CTF machine**.



## Target Information
- Target IP: `10.0.2.4`  
- Attacker IP: `10.0.2.5`  



## Directory Enumeration
Used **dirb** to brute-force hidden directories:

```bash
dirb http://10.0.2.4/
```
### Discovered Directories
- `/backups/`
- `/batch/`
- `/core/`
- `/css/`
- `/images/`
- `/install/`
- `/js/`
- `/secret/` ⬅️ suspicious!
- `/uploads/`
___
### Findings
- The `/secret/` directory contained a suspicious image file (`doubletrouble.jpg`).
- Likely candidate for **steganography exploitation** (hidden data embedded).
