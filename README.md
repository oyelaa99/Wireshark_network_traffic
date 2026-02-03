This version incorporates your specific explanations and website examples while maintaining a high-quality GitHub format.
Wireshark Network Traffic Forensics & Protocol Analysis
📖 Project Description
This project features a deep-dive analysis of various network protocols and security scenarios using Wireshark. It demonstrates security auditing and traffic pattern recognition through packet-level inspection.
The repository includes detailed analysis reports and custom Wireshark filters used to identify latencies and security vulnerabilities in modern network environments.
🎯 Key Learning Objectives

    Encapsulation & Decapsulation: Visualizing how data travels through the OSI layers.
    The TCP Three-Way Handshake: Analyzing sequence/acknowledgment numbers and flow control.
    Security Auditing: Identifying plaintext credentials in unencrypted traffic (HTTP, FTP, Telnet).

🔍 Analysis Scenarios
Scenario 01: The "Naked" Web (HTTP vs. HTTPS)
In this scenario, I inspect HTTP and HTTPS packets to illustrate the vital importance of TLS encryption. I visited http://www.pentest-standard.org, a well-known platform used by ethical hackers. Despite its reputation, it does not use an "S" at the end of HTTP, meaning the site is not secure.

    Discovery: After analyzing the pcap, I discovered I could see the entire content of the HTML file visited in cleartext.
    Insight: This proves that without encryption, any data exchanged is visible to anyone on the network path.
    (See figure below)

Scenario 02: The HANDSHAKE
This analysis focuses on the process where the server and client "shake hands" to establish a connection by agreeing on common terms.

    The Process: I captured the three-step process (SYN, SYN-ACK, and ACK) used to ensure data reaches the correct receiver.
    Transmission: Post-handshake, I analyzed how TCP manages reliability, ordering, and flow control using the Window Size.
    Termination: Finally, I captured the connection closure where both parties agree to stop the session (FIN-ACK, FIN-ACK).

Scenario 03: The Credential Leak (FTP vs. SFTP)
Continuing with the importance of secure data transmission, I showcased the critical risk of using FTP instead of SFTP.

    Discovery: After connecting to an FTP server with credentials and analyzing the packets, I was able to easily extract the username and password from the traffic stream.
    Conclusion: This highlights why secure protocols are mandatory for sensitive information transfer.
    (See picture below)

Scenario 04: Attack Simulation (TCP SYN Flood)
For the final part, I moved to the attacker’s perspective to simulate a DoS attack based on a TCP SYN Flood.

    Methodology: By sending thousands of SYN requests via hping3, I forced the server to keep part of its memory waiting for the remaining part of the 3-way handshake.
    Result: The server becomes exhausted from these "half-open" connections, eventually leading to a service crash or unavailability for legitimate users.

🛡️ Technical Mitigations
To defend against the vulnerabilities identified:

    SYN Cookies: Enable SYN Cookies on servers to prevent memory exhaustion during a flood.
    Protocol Hardening: Enforce SFTP (SSH File Transfer Protocol) and HSTS (HTTP Strict Transport Security) to prevent users from accessing unsecure versions of websites.

📂 Repository Structure
text

├── reports/              # Detailed PDF analysis for each capture
├── screenshots/          # Visual evidence of filters and streams
├── filters_cheatsheet.md # Library of custom Wireshark display filters
└── README.md             # Project documentation

Use code with caution.
🛠️ Tools & Technologies

    Packet Analyzer: Wireshark
    Traffic Generation: Hping3 (sudo hping3 -S --flood --rand-source [Target_IP] -p 80)
    Environment: Ubuntu / Kali-Linux
    Protocols: TCP, UDP, HTTP, HTTPS (TLS), DNS, FTP, QUIC
