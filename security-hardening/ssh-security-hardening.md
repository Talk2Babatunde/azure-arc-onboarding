# SSH Security Hardening (Azure Ubuntu VM)

This guide documents the steps I performed to harden SSH access on an Ubuntu virtual machine connected via Azure Arc, based on Defender for Cloud recommendations.

## 🔍 Initial State

The VM had:
- Password authentication enabled 
- Port 22 open to the internet
- No brute-force protections

![Initial SSH State](images/ssh-before.png)

## 🔧 Hardening Steps

1. **Disabled Password Authentication**
   ```bash
   sudo nano /etc/ssh/sshd_config

