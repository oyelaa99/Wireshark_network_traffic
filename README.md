
---

# Wireshark Network Traffic Forensics & Protocol Analysis

## 📖 Project Description

This project features a deep-dive analysis of various network protocols and security scenarios using **Wireshark**. It demonstrates security auditing, and traffic pattern recognition.

The repository includes captured `.pcapng` files, detailed analysis reports, and custom Wireshark filters used to identify latencies and security vulnerabilities in modern network environments.

---

## 🎯 Key Learning Objectives

* **Encapsulation & Decapsulation:** Visualizing how data travels through the OSI layers.
* **The TCP Three-Way Handshake:** Analyzing sequence/acknowledgment numbers and flow control.
* **Security Auditing:** Identifying plaintext credentials in unencrypted traffic (HTTP, FTP, Telnet).


---

## 🛠️ Lab Setup & Scenarios

The lab was staged across four distinct scenarios captured in an isolated environment to ensure high-fidelity data.

| Scenario | Analysis Focus | Key Learning |
| --- | --- | --- |
| **01: The "Naked" Web** | HTTP vs. HTTPS (TLS) | Inspecting GET/POST requests and why SSL/TLS is vital. |
| **02: The Handshake** | Full TCP Sessions | Deep dive into SYN, SYN-ACK, ACK, and FIN/RST flags. |
| **03: The Leak** | Unencrypted FTP/Telnet | Capturing plaintext credentials via "Follow TCP Stream." |
| **04: Attack Simulation** | TCP SYN Flood | Visualizing server exhaustion from half-open connections. |

---

## 🔍 Analysis Highlights

### 1. The TCP Three-Way Handshake

* **Objective:** Analyze the reliability of connection-oriented communication.
* **Observation:** Captured the full `SYN` → `SYN-ACK` → `ACK` sequence.
* **Key Finding:** Validated how sequence numbers increment to ensure data integrity and ordered delivery.
* **Primary Filter:** `tcp.flags.syn == 1`

### 2. Security Audit: Plaintext Credential Leakage

* **Objective:** Demonstrate the risks of using legacy unencrypted protocols.
* **Action:** Captured traffic during a simulated login to an FTP server.
* **Discovery:** Successfully recovered a username and password in cleartext using the **"Follow TCP Stream"** feature.
* **Mitigation:** Implementation of SFTP/SSH to prevent MITM (Man-in-the-Middle) attacks.

### 3. Network Performance: Latency & Retransmission

* **Objective:** Identify the root cause of application latency.
* **Observation:** High volume of **TCP Retransmissions** and **Duplicate ACKs** indicated significant packet loss.

---

## 📂 Repository Structure

```text
├── pcaps/                # Raw .pcapng files for each scenario
├── reports/              # Detailed PDF analysis for each capture
├── screenshots/          # Visual evidence of filters and streams
├── filters_cheatsheet.md # Library of custom Wireshark display filters
└── README.md             # Project documentation

```

---

## 🛠️ Tools & Technologies

* **Packet Analyzer:** Wireshark
* **Traffic Generation:**  Hping3
* **Environment:** ubuntu / kali-linux
* **Protocols:** TCP, UDP, HTTP, HTTPS (TLS), DNS, FTP, QUIC

---

## 📈 Key Skills Demonstrated

* **Traffic Forensics:** Reconstructing multi-packet "conversations" from raw data.
* **Security Mindset:** Identifying misconfigurations and cleartext vulnerabilities.
* **Filter Logic:** Expertise in complex display filters to isolate malicious traffic.
* **OSI Layer Knowledge:** Deep understanding of Layer 2 (Data Link) through Layer 7 (Application).

---

