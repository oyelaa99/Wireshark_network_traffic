
---

#  Wireshark Network Traffic Forensics & Protocol Analysis

## 📖 Project Description

This project presents an in-depth forensic analysis of network traffic and protocol behavior using **Wireshark**.
It demonstrates hands-on skills in **network security auditing**, **packet-level inspection**, and **traffic pattern recognition** across multiple real-world scenarios.

The repository includes:

* Detailed analysis reports
* Custom Wireshark display filters
* Visual packet capture evidence highlighting security flaws and performance insights

---

## 🎯 Key Learning Objectives

* **Encapsulation & Decapsulation**
  Visualizing how data traverses the OSI layers

* **TCP Three-Way Handshake**
  Analyzing sequence numbers, acknowledgments, and flow control

* **Security Auditing**
  Identifying plaintext credentials in unencrypted protocols (HTTP, FTP, Telnet)

---

##  Analysis Scenarios

###  Scenario 01: The *"Naked"* Web (HTTP vs HTTPS)

This scenario demonstrates the security risks of using **unencrypted HTTP** instead of HTTPS.

* **Target Website:** `http://www.pentest-standard.org`
  A well-known ethical hacking resource that surprisingly does **not** enforce HTTPS

* **Discovery:**
  Packet capture analysis revealed the **entire HTML content** transmitted in cleartext

* **Insight:**
  Without TLS encryption, all transmitted data can be intercepted and read by any attacker on the network path

> 📌 **Note:** See *Figure 1* in the `/screenshots` folder for packet capture evidence

---

###  Scenario 02: The TCP *HANDSHAKE*

This analysis focuses on how TCP establishes, maintains, and terminates reliable connections.

* **Connection Setup:**
  Captured the full **3-way handshake**:

  * `SYN`
  * `SYN-ACK`
  * `ACK`

* **Data Transmission:**
  Analyzed reliability, ordering, and flow control using:

  * Sequence numbers
  * Acknowledgments
  * TCP Window Size

* **Connection Termination:**
  Observed proper session closure:

  * `FIN-ACK`
  * `FIN-ACK`

---

###  Scenario 03: Credential Leak (FTP vs SFTP)

This scenario highlights the dangers of legacy file transfer protocols.

* **Discovery:**
  Using **FTP**, credentials were easily extracted from captured packets using:

  ```
  Follow → TCP Stream
  ```

* **Conclusion:**
  FTP transmits usernames and passwords in **cleartext**, making it unsuitable for sensitive data transfer

> 📌 **Note:** See *Figure 3* in the `/screenshots` folder for cleartext credential leakage

---

###  Scenario 04: Attack Simulation (TCP SYN Flood)

A **Denial-of-Service (DoS)** attack was simulated using a TCP SYN Flood.

* **Methodology:**
  Thousands of SYN packets were sent to the target server, forcing it to maintain **half-open connections**

* **Result:**
  Server memory becomes exhausted, preventing legitimate users from establishing connections

```bash
sudo hping3 -S --flood --rand-source <Target_IP> -p 80
```

---

##  Technical Mitigations

To mitigate the identified vulnerabilities:

* **SYN Cookies**
  Prevent memory exhaustion during SYN Flood attacks

* **Protocol Hardening**
  Enforce **HSTS (HTTP Strict Transport Security)** to block insecure HTTP access

* **Encrypted Transfers**
  Require **SFTP or SSH** for all file transfers

---

---

## 🛠️ Tools & Technologies

* **Packet Analyzer:** Wireshark
* **Traffic Generation:** Hping3
* **Operating Systems:** Ubuntu, Kali Linux
* **Protocols Analyzed:**

  * TCP
  * UDP
  * HTTP / HTTPS (TLS)
  * DNS
  * FTP
  * QUIC

---

## 📌 Disclaimer

This project was conducted in a **controlled lab environment** for educational and defensive security purposes only.

---
