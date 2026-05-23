# 🌐 Wireshark Lab: Network Traffic & Protocol Analysis

## 📝 Project Overview
This project demonstrates how to capture, filter, and inspect Network Layer and Application Layer traffic using **Wireshark**. By generating targeted network traffic on a local machine, this lab breaks down foundational core concepts including **DNS resolution**, the **TCP Three-Way Handshake**, **cleartext credential vulnerabilities**, and **TCP stream reconstruction**.

---

## 🛠️ Environment & Tools
* **Packet Analyzer:** Wireshark 
* **Operating System:** [e.g., Windows 11 / macOS / Ubuntu Linux] 
* **Command Line Utilities:** `nslookup`, PowerShell/Terminal 

---

## 🔍 Key Concepts Covered
* **Packets & Protocols:** Understanding structure, headers, and payloads.
* **The TCP 3-Way Handshake:** Analyzing connection states via `SYN`, `SYN-ACK`, and `ACK` flags.
* **Domain Name System (DNS):** Verifying A-record queries and server responses.
* **Unencrypted Traffic Risk:** Spotting cleartext credentials over standard HTTP.

---

## 🚀 Guided Exercises & Walkthrough


---

### 🔹 Exercise A — Capture a DNS Lookup
**Objective:** Generate a manual DNS query using the `nslookup` command-line utility and capture the A-record query and response within Wireshark.

1. Initiated a live capture on the active network interface in Wireshark.
2. Executed a targeted query via the local terminal:
   ```bash
   nslookup google.com
📸 Screenshot:
Terminal output showing the resolved IP addresses:
<img width="1000" alt="image" src="https://github.com/DavidPatrick92/Wireshark_-_Network_Analysis/blob/main/images/nslookup.png">

3. Isolated the traffic in Wireshark using the display filter: dns
📸 Screenshot:
Wireshark packet list with the applied dns filter:
<img width="1000" alt="image" src="https://github.com/DavidPatrick92/Wireshark_-_Network_Analysis/blob/main/images/DNS%20Response.png">

5. Analyzed the Standard  Query A packet and its matching Standard Query Response.
📸 Screenshot:
Expanded "Domain Name System (response)" detail panel matching the terminal IP output:
<img width="1000" alt="image" src="https://github.com/DavidPatrick92/Wireshark_-_Network_Analysis/blob/main/images/DNS%20Packet%20Details.png">
  
🔹 Exercise B — Watch the TCP Three-Way Handshake
Objective: Capture and analyze the precise connection sequence established between a client machine and an HTTP server.
1. Started a live packet capture and navigated to http://example.com in a web browser.
2. Located the server's IP address and isolated the conversation using the filter:
   tcp and ip.addr == [Server_IP]
3. Verified the exact three sequential packets making up the handshake sequence:
    Packet 1 (SYN): Client connection request.
    Packet 2 (SYN, ACK): Server connection acceptance and acknowledgment.
    Packet 3 (ACK): Client connection confirmation.
   📸 Screenshot Placeholders:
   Sequential SYN → SYN-ACK → ACK packets highlighted in the Wireshark main window:
<img width="1000" alt="image" src="https://github.com/DavidPatrick92/Wireshark_-_Network_Analysis/blob/main/images/Wirehshark(TCP%20Three-Way%20Handshake).png">   

🔹 Exercise C — Spot Cleartext Credentials (HTTP)
Objective: Visually demonstrate the security risks associated with unencrypted web applications by capturing sensitive payloads over raw HTTP.
1. Launched a capture and submitted a dummy username and password on a testing HTTP application form.
2. Filtered for outbound submission payloads using the display filter:
   http.request.method == POST
3.Drilled down into the HTML Form URL Encoded layer within the packet detail pane.
📸 Screenshot Placeholders:
Plaintext username and password parameters exposed within the packet details:
<img width="1000" alt="image" src="https://github.com/DavidPatrick92/Wireshark_-_Network_Analysis/blob/main/images/Login%20Credentials.png">

🔹 Exercise D — Follow a Full TCP Stream
Objective: Reassemble fragmented, independent network packets back into a cohesive, human-readable conversation.
1. Right-clicked an HTTP packet within the traffic history list.
2. Selected Follow ➡️ TCP Stream to view the raw conversation data.
3. Audited the full layout (Red text representing client browser requests; Blue text representing server-side replies)
📸 Screenshot Placeholders:
The reassembled TCP stream conversation layout box showing the HTTP data stream context:
<img width="1000" alt="image" src="https://github.com/DavidPatrick92/Wireshark_-_Network_Analysis/blob/main/images/TCP%20Stream%20Follow.png">

## 📈 Key Technical Takeaways & Professional Insights

Implementing this network analysis lab provided deep, hands-on experience with packet-level telemetries, mapping directly to the daily responsibilities of a Security Operations Center (SOC) Analyst or Cloud Security Engineer.

### 1. Packet Protocol Deep-Dives
* **The Concept:** Dissected the foundational DNA of network conversations across the OSI model, analyzing raw TCP three-way handshakes (`SYN`, `SYN-ACK`, `ACK`), DNS queries, and cryptographic TLS handshakes.
* **Real-World Analogy:** Looking at a network without a packet analyzer is like a building security guard watching people enter a lobby from a distance. Utilizing Wireshark is like opening every single delivery package at the checkpoint, verifying the physical manifest, and checking the sender's true ID before letting them pass.

### 2. Slicing Through Network Noise via Display Filters
* **The Concept:** Mastered complex Wireshark display syntax (e.g., isolating specific subnets, tracing persistent TCP streams, and hunting for unencrypted cleartext protocols like HTTP or FTP).
* **Real-World Analogy:** A busy network interface card captures hundreds of thousands of packets a minute—it’s a deafening roar of data. Writing a precise display filter is like putting on noise-canceling headphones tuned exclusively to a single whisper across a crowded stadium, allowing an investigator to isolate a threat instantly.

### 3. Fingerprinting Anomalous Patterns & Malicious Signatures
* **The Concept:** Isolated indicators of compromise (IoCs) by tracking fragmented packets, identifying irregular high-velocity traffic spikes (DDoS indicators), and analyzing failed authentication streams.
* **Real-World Analogy:** Normal network traffic has a predictable rhythm, much like regular foot traffic in a bank. Spotting malicious signatures via packet analysis is like noticing someone walking through the bank lobby wearing a ski mask and pacing back and forth near the vault-it immediately stands out as an actionable security event.

### 4. Forensic Mindset & Incident Root-Cause Analysis
* **The Concept:** Moved past superficial error messages to uncover the exact structural layer where a network transmission failed, drastically reducing the Mean Time to Resolution (MTTR).
* **Real-World Analogy:** When a cloud application goes down, a standard administrator looks at a generic "Connection Timed Out" webpage. A security professional pulls a packet capture (`.pcap`) to prove exactly whether a firewall dropped the packet, a routing table misplaced it, or a host server refused the connection.


