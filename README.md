Here is your project formatted into a professional, clean GitHub `README.md`. I have optimized the layout, added clear hierarchies, and included placeholders for your screenshots to make the repository look polished for recruiters.

---

# Wireshark Network Traffic Forensics & Protocol Analysis

## 📖 Project Description

This project features a deep-dive analysis of various network protocols and security scenarios using **Wireshark**. It demonstrates proficiency in packet-level troubleshooting, security auditing, and traffic pattern recognition.

The repository includes captured `.pcapng` files, detailed analysis reports, and custom Wireshark filters used to identify latencies and security vulnerabilities in modern network environments.

---

## 🎯 Key Learning Objectives

* **Encapsulation & Decapsulation:** Visualizing how data travels through the OSI layers.
* **The TCP Three-Way Handshake:** Analyzing sequence/acknowledgment numbers and flow control.
* **Security Auditing:** Identifying plaintext credentials in unencrypted traffic (HTTP, FTP, Telnet).
* **Troubleshooting:** Utilizing IO Graphs and Flow Graphs to spot network bottlenecks.

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
* **Analysis:** Utilized **IO Graphs** to correlate traffic spikes with latency patterns.

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
* **Traffic Generation:** Nmap, Hping3
* **Environment:** Kali Linux / Windows 11
* **Protocols:** TCP, UDP, HTTP, HTTPS (TLS), DNS, ARP, FTP, QUIC

---

## 📈 Key Skills Demonstrated

* **Traffic Forensics:** Reconstructing multi-packet "conversations" from raw data.
* **Security Mindset:** Identifying misconfigurations and cleartext vulnerabilities.
* **Filter Logic:** Expertise in complex display filters to isolate malicious traffic.
* **OSI Layer Knowledge:** Deep understanding of Layer 2 (Data Link) through Layer 7 (Application).

---

### Next Step for your Repo:

To make this truly stand out, you should create the `filters_cheatsheet.md` file mentioned in the structure. **Would you like me to generate a list of the most important Wireshark filters you should include in that file?**
