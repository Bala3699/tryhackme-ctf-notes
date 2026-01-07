# 📘 TryHackMe Lab Documentation – C2 Detection (Blue Team)

## Lab Overview

This documentation covers a **TryHackMe Blue Team lab** focused on detecting **Command and Control (C2)** traffic using network traffic analysis. The objective of the lab is to identify compromised hosts by analyzing beaconing behavior rather than inspecting payloads.

This lab reflects real-world **SOC Analyst / Threat Hunter** workflows.

---

## Objectives

* Understand Command and Control (C2) communication
* Detect beaconing behavior in network traffic
* Analyze logs generated from packet captures
* Use metadata-based detection techniques

---

## Environment

* Platform: TryHackMe
* Role: Blue Team / SOC Analyst
* Data Source: Network traffic (PCAP)

---

## Methodology

1. Traffic capture provided by the lab was analyzed
2. Logs were generated from the PCAP
3. Beaconing patterns were identified
4. Suspicious hosts were isolated
5. C2 communication characteristics were confirmed

---

## Key Indicators Observed

* Regular interval connections
* Repeated destination IPs
* Low data volume per connection
* Consistent session timing

---

## Outcome

* Successfully identified C2 beaconing traffic
* Understood attacker persistence mechanisms
* Gained hands-on SOC threat hunting experience

---

## Skills Demonstrated

* Network Traffic Analysis
* Threat Hunting
* Blue Team Investigation
* SOC Workflow Understanding

---

## Disclaimer

This lab was performed in a controlled educational environment. No real-world systems were harmed.

---

# 🛠️ Tool Documentation – Zeek & RITA (with Commands)

## 🔹 Zeek Documentation

### What is Zeek?

Zeek is a network security monitoring tool that converts packet captures into high-level logs for analysis.

### Installing Zeek

```bash
sudo apt update
sudo apt install zeek
```

### Running Zeek on a PCAP

```bash
zeek -r traffic.pcap
```

### Important Zeek Logs

* conn.log – connection metadata
* dns.log – DNS queries
* http.log – HTTP requests
* ssl.log – TLS connections

Zeek does not alert by default; it provides structured logs for further analysis.

---

## 🔹 RITA Documentation

### What is RITA?

RITA (Real Intelligence Threat Analytics) detects beaconing and C2 behavior by analyzing Zeek logs.

### Installing RITA

```bash
sudo apt install golang
sudo git clone https://github.com/activecm/rita.git
cd rita
make
```

### Importing Zeek Logs

```bash
rita import zeek_logs c2-dataset
```

### Running Beacon Analysis

```bash
rita analyze c2-dataset
```

### Viewing Results

```bash
rita show-beacons c2-dataset
```

---

## How Zeek & RITA Work Together

1. Zeek converts raw traffic into logs
2. RITA analyzes those logs
3. Beaconing patterns are detected
4. Suspicious hosts are identified

---

## Use Case in SOC

* Detect malware callbacks
* Identify compromised systems
* Support incident response
* Enhance threat hunting

---

## Conclusion

This toolchain demonstrates real-world **SOC-grade C2 detection** using open-source tools and is directly applicable to blue team operations.

---

## Author

**Balamurugan**
Cybersecurity | Blue Team | SOC Analyst
