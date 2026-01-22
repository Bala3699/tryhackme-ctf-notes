# 🎄 ICS / SCADA Security – Modbus Exploitation & Remediation

**TryHackMe: ICS/Modbus – Claus for Concern**  
*Advent of Cyber 2025 – Day 19*

---

## 📌 Overview

This repository documents the successful completion of the **TryHackMe – ICS/Modbus: Claus for Concern** room.  
The lab focuses on identifying, analysing, and safely remediating **Industrial Control System (ICS)** vulnerabilities using the **Modbus TCP protocol**.

The scenario simulates a compromised **SCADA-controlled drone delivery system**, where an attacker manipulates **PLC registers and coils** to sabotage operations.

⚠️ **All actions were performed in an authorised TryHackMe lab environment.**

---

## 🎯 Objectives

- Understand **SCADA & PLC architecture**
- Learn how **Modbus TCP (port 502)** operates
- Identify **unauthenticated Modbus vulnerabilities**
- Perform ICS reconnaissance using **Python**
- Safely restore system state **without triggering safety traps**
- Gain hands-on exposure to **ICS incident response**

---

## 🏭 Technologies & Tools Used

- SCADA / PLC Concepts  
- Modbus TCP Protocol  
- Python 3  
- PyModbus (v3.6.8)  
- Nmap  
- TryHackMe AttackBox (Linux)

---

## 🔍 Attack Surface Identified

| Port | Service | Description |
|-----|--------|-------------|
| 22 | SSH | Remote management |
| 80 | HTTP | CCTV monitoring feed |
| 502 | Modbus TCP | PLC control (unauthenticated) |

**Key Finding:**  
Modbus TCP allows **read/write access without authentication**, making it a **critical ICS vulnerability**.

---

## 🧠 ICS Architecture Overview

### SCADA Components Identified

- **Sensors & Actuators** – Physical operations  
- **PLC (Programmable Logic Controller)** – Automation logic  
- **Monitoring Systems** – CCTV feed (HTTP)  
- **Modbus TCP Server** – Direct control channel  
- **Historians & Logs** – Disabled by attacker  

---

## ⚠️ Vulnerabilities Observed

- ❌ No authentication on Modbus (port 502)
- ❌ No encryption (plaintext traffic)
- ❌ No access control on registers & coils
- ❌ Safety and audit logging disabled
- ❌ PLC logic manipulation possible

---

## 🧪 Modbus Reconnaissance

### Key Registers & Coils

| Type | Address | Function |
|----|--------|----------|
| HR0 | Holding Register | Package Type Selector |
| HR1 | Holding Register | Delivery Zone |
| HR4 | Holding Register | Attacker Signature |
| C10 | Coil | Inventory Verification |
| C11 | Coil | Protection Mechanism |
| C12 | Coil | Emergency Dump |
| C13 | Coil | Audit Logging |
| C15 | Coil | Self-Destruct Mechanism |

---

## 🛠️ Reconnaissance Script

A Python script was used to:
- Read holding registers
- Read coil states
- Detect attacker signatures
- Identify safety traps

📁 **File:** `reconnaissance.py`

### Key Findings
- Package type forced to **Chocolate Eggs**
- Audit logging disabled
- Inventory verification disabled
- Protection mechanism enabled
- Attacker signature detected

---

## 🚨 Trap Mechanism Analysis

### ⚠️ Critical Logic Trap Identified

If:
- **HR0** is modified while  
- **C11 (Protection Mechanism)** is enabled  

Then:
- **C15 (Self-Destruct)** is armed
- 30-second countdown begins
- Emergency dump redirects inventory to ocean zone

This highlights why **ICS remediation order is critical**.

---

## 🧯 Safe Remediation Strategy

Correct remediation order followed:

1. Disable protection mechanism (`C11 = False`)
2. Restore correct package type (`HR0 = 0`)
3. Enable inventory verification (`C10 = True`)
4. Enable audit logging (`C13 = True`)
5. Verify self-destruct was not triggered

📁 **File:** `restore_christmas.py`

---

## ✅ Outcome

- 🎁 Christmas deliveries restored
- 🛑 Emergency dump prevented
- 🔍 Audit logging re-enabled
- 🚫 Self-destruct avoided

---

## 🧠 Key Learning Outcomes

- ICS protocols prioritise **availability over security**
- Modbus TCP is **high-risk when exposed**
- PLC logic manipulation can cause **real-world damage**
- ICS incident response requires **deep protocol awareness**
- Incorrect remediation can trigger **physical consequences**

---

## 🛡️ Security Recommendations

- Restrict Modbus access using **firewalls**
- Segment PLCs into **OT networks**
- Use **VPNs & secure gateways**
- Enable continuous **monitoring & logging**
- Deploy **IDS/IPS for ICS traffic**
- Never expose Modbus directly to IT networks

---

## 📚 References

- TryHackMe – *ICS/Modbus: Claus for Concern*
- Modbus Protocol Specification
- ICS-CERT Security Best Practices
- NIST SP 800-82 – *ICS Security*

---

## ⚖️ Disclaimer

This project is for **educational purposes only**.  
All activities were conducted in a **legal, controlled lab environment** provided by TryHackMe.

---

## ⭐ Author

**Balamurugan**  
Cybersecurity | Ethical Hacking | ICS & Network Security  
TryHackMe | GitHub
