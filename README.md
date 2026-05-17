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


