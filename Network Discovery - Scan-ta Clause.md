# 👨🏾‍💻 TryHackMe: Discovering Exposed Services

**Author:** Balamutugan
**Platform:** TryHackMe
**Room Focus:** Service Discovery, Nmap, FTP, Custom Services, DNS, Local Enumeration

---

## 1. Objective

The goal of this lab was to regain access to a compromised QA server (`tbfc-devqa01`) by discovering exposed services, extracting hidden keys, and retrieving the final flag from a local database.

---

## 2. Target Information

* **Machine Name:** tbfc-devqa01
* **Target IP:** MACHINE_IP
* **Attacker Machine:** TryHackMe AttackBox / VPN-connected Kali Linux

---

## 3. Initial Reconnaissance (TCP Port Scan)

A basic Nmap scan was performed to identify commonly exposed services.

```bash
nmap MACHINE_IP
```

### Result

* **22/tcp** – SSH
* **80/tcp** – HTTP

The web server was accessible and showed a defaced page with the message:

> **"Pwned by HopSec"**

---

## 4. Full TCP Port Scan (All Ports)

To identify non-standard services, a full port scan was executed with banner grabbing.

```bash
nmap -p- --script=banner MACHINE_IP
```

### Discovered Services

| Port  | Service | Details          |
| ----- | ------- | ---------------- |
| 22    | SSH     | OpenSSH 9.6p1    |
| 80    | HTTP    | Web server       |
| 21212 | FTP     | vsFTPd 3.0.5     |
| 25251 | Custom  | TBFC maintd v0.2 |

---

## 5. FTP Enumeration (Key 1)

The FTP service was running on a non-standard port and allowed anonymous login.

```bash
ftp MACHINE_IP 21212
```

```text
Name: anonymous
```

### Files Found

* `tbfc_qa_key1`

```bash
get tbfc_qa_key1 -
```

### Key 1

> 🔒 **Redacted** – Key value intentionally not documented for security reasons.

---

## 6. Custom Service Enumeration via Netcat (Key 2)

The custom TBFC maintenance service was accessed using Netcat.

```bash
nc -v MACHINE_IP 25251
```

```text
Commands: HELP, STATUS, GET KEY, QUIT
```

### Command Executed

```text
GET KEY
```

### Key 2

> 🔒 **Redacted** – Key value intentionally not documented for security reasons.

---

## 7. UDP Port Scanning & DNS Enumeration (Key 3)

UDP ports were scanned to discover hidden services.

```bash
nmap -sU MACHINE_IP
```

### Result

* **53/udp** – DNS

A DNS TXT record was queried using `dig`.

```bash
dig @MACHINE_IP TXT key3.tbfc.local +short
```

### Key 3

> 🔒 **Redacted** – Key value intentionally not documented for security reasons.

---

## 8. Key Combination

> 🔐 **Combined key not shown** – Sensitive authentication data omitted from documentation.

---

## 9. On-Host Service Discovery

Once inside the admin console, listening services were enumerated locally.

```bash
ss -tunlp
```

### Notable Internal Services

* **3306/tcp** – MySQL (localhost only)

---

## 10. MySQL Enumeration & Flag Retrieval

The local MySQL database was accessed without authentication.

```bash
mysql -D tbfcqa01 -e "show tables;"
mysql -D tbfcqa01 -e "select * from flags;"
```

### Final Flag

> 🏁 **Flag redacted** – Not included to maintain platform integrity.

---

# 📘 Nmap Usage in This Lab

## Purpose of Nmap

Nmap was used for:

* Identifying exposed TCP services
* Discovering services on non-standard ports
* Enumerating UDP-based services

---

## Nmap Commands Used

### 1. Basic TCP Scan (Top 1000 Ports)

```bash
nmap MACHINE_IP
```

* Fast reconnaissance
* Identifies common services

---

### 2. Full TCP Port Scan with Banner Grabbing

```bash
nmap -p- --script=banner MACHINE_IP
```

* Scans all 65,535 TCP ports
* Reveals service banners
* Detects non-standard service ports

---

### 3. UDP Port Scan

```bash
nmap -sU MACHINE_IP
```

* Identifies UDP services
* Used to detect DNS on port 53

---

## Key Takeaways from Nmap

* Services often run on non-default ports
* Banner grabbing helps identify software versions
* UDP scanning is essential for complete visibility
* Nmap is a foundational tool for SOC and penetration testing

---

## 11. Conclusion

This room demonstrated real-world service discovery techniques using Nmap, FTP, Netcat, DNS, and local enumeration. Proper port scanning and service analysis led to full system compromise and flag recovery.

✅ **Skills Gained:**

* Network service discovery
* TCP & UDP scanning
* Banner grabbing
* Internal service enumeration
* Database extraction

---

