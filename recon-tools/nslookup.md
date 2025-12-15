# 🛠️ Tool Documentation: nslookup

## 📌 Tool Name

**nslookup (Name Server Lookup)**

---

## 🎯 Purpose of the Tool

`nslookup` is a network administration and reconnaissance tool used to query the **Domain Name System (DNS)**. It helps in retrieving information related to domain names, IP addresses, and DNS records.

In ethical hacking and CTF environments like **TryHackMe**, it is mainly used during the **reconnaissance phase**.

---

## 🧠 Why nslookup is Important in CTFs

DNS is a critical part of web infrastructure. By analyzing DNS records, a security learner can:

* Understand how a domain is structured
* Identify connected servers
* Gain insights into network configuration
* Support further enumeration

---

## 🧩 Areas of Usage

* DNS enumeration
* Web reconnaissance
* Network analysis
* Initial information gathering

---

## ⚙️ Basic Syntax

```
nslookup <domain-name>
```

Example:

```
nslookup example.com
```

---

## 🔍 Information That Can Be Retrieved

Using `nslookup`, the following DNS details can be analyzed:

* IP address of a domain (A record)
* Mail exchange servers (MX records)
* Name servers (NS records)
* Canonical name records (CNAME)
* DNS server response details

---

## 🧪 Usage in TryHackMe (High-Level Overview)

In TryHackMe CTF rooms, `nslookup` is used as follows:

1. A target domain is provided
2. DNS queries are performed
3. Results are analyzed for useful information
4. Findings are used for further learning and enumeration

> This documentation does **not** include flags, payloads, or challenge solutions.

---

## 🧠 Learning Outcomes

Through practicing with `nslookup`, the following concepts were learned:

* How DNS resolution works
* The relationship between domains and IP addresses
* The role of DNS in web security
* Importance of DNS information in reconnaissance

---

## 🛡️ Defensive Security Perspective

From a defensive viewpoint, this tool highlights:

* Why DNS records should be carefully configured
* How excessive DNS exposure can leak information
* The importance of DNS hardening and monitoring

---

## ⚠️ Ethical Usage Notice

This tool was used **only in legal and educational environments**, such as:

* TryHackMe labs
* CTF practice platforms
* Cybersecurity learning scenarios

No real-world systems were targeted.

---

## 🔗 Practice Platform

* Platform: **TryHackMe**
* Domain: Ethical Hacking & Cybersecurity

---

## 📌 Documentation Type

 Learning-focused
 Ethical & professional
 Recruiter-safe
 No sensitive content

