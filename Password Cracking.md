# 🔐 Password Cracking – Dictionary & Mask Attacks (TryHackMe)

## 📌 Overview
This repository documents a **TryHackMe practical lab** focused on recovering weak passwords protecting encrypted files.  
Rather than breaking cryptographic algorithms, attackers exploit **human weaknesses** such as predictable and reused passwords.

This lab demonstrates **offline password cracking techniques** and also highlights **blue‑team detection and response considerations**.

---

## 🎯 Learning Objectives
- Understand real-world password cracking concepts  
- Identify encrypted file types before cracking  
- Perform dictionary-based password attacks  
- Understand brute-force and mask-based attacks  
- Learn detection opportunities from a SOC perspective  

---

## 🧰 Tools Used

| Tool | Purpose |
|-----|--------|
| `file` | Identify file type |
| `pdfcrack` | Crack password-protected PDF files |
| `john` (John the Ripper) | Password cracking framework |
| `pdf2john` | Convert PDF to crackable hash |
| `zip2john` | Convert ZIP to crackable hash |
| `rockyou.txt` | Common leaked password wordlist |

---

## 🛠️ Environment Setup
Navigate to the working directory:

```bash
cd ~/Desktop/password_cracking
```
## To Check file contents:
```
ls
```
## 🔍 Step 1: Identify the Encrypted File

Before choosing a cracking tool, identify the file type.
```
file secure_file
```
### Example Output:
```
secure_file: PDF document,  version 1.7, encrypted 
```
✔️ This confirms the file is an encrypted PDF.

## 📘 Step 2: Dictionary Attack Using pdfcrack

A dictionary attack tests passwords from a known wordlist.
```
pdfcrack -f secure_file -w /usr/share/wordlists/rockyou.txt
```
###  Explanation:

- `-f` → Target file
-  `-w` → Wordlist used
-  Tests thousands of common passwords efficiently
###  Sample Output:
```
found user-password: password123
```
## 🔄 Alternative Method: Using John the Ripper
###  Convert PDF to Hash
```
pdf2john secure_file > hash.txt
```
###  Crack Using Wordlist
```
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```
###  Show Cracked Password
```
john --show hash.txt
```
## 🔐 ZIP File Password Cracking (If Applicable)
###  Convert ZIP to Hash
```
zip2john secure.zip > ziphash.txt
```
###  Crack ZIP Password
```
john --wordlist=/usr/share/wordlists/rockyou.txt ziphash.txt
```
## 🧠 Understanding Mask Attacks

When password structure is known, mask attacks reduce cracking time.

### Example:

If password format is known:
```
Capital letter + 4 lowercase + 2 digits
```

### John Mask Attack:
```
john --mask='?u?l?l?l?l?d?d' hash.txt
```
## 🛡️ Blue Team Perspective – Detection & Defense
### 🚨 Indicators of Password Cracking

-  High CPU usage by unknown processes

-  Access to sensitive files outside normal hours

-  Repeated file access attempts

-  Hash extraction from PDFs or ZIP files

### 🧪 Detection Tools

-  Sysmon

-  Auditd

-  EDR solutions

-  File integrity monitoring
---
###  🔐 Security Best Practices

-  Use long, random passwords

-  Enforce password managers

-  Disable password-only encryption for sensitive data

-  Enable MFA wherever possible

-  Monitor endpoint activity continuously
---
###  🧪 TryHackMe Skills Demonstrated

-  Offensive password cracking

-  File type analysis

-  Tool selection & execution

-  Defensive detection mindset
---

<br>

<br>

##  ⚠️ Disclaimer

This repository is for educational purposes only.
All techniques demonstrated were performed in legal lab environments such as TryHackMe.
Do not use these methods on systems you do not own or have permission to test.
---
## 👤 Author

Balamutugan
Cybersecurity Enthusiast | Ethical Hacking | SOC & Blue Team
TryHackMe Practitioner
