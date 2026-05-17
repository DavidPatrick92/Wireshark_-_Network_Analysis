🌐 Wireshark Lab: DNS Packet Analysis
📝 Project Overview
This project demonstrates how to capture, filter, and analyze Network Layer and Application Layer traffic using Wireshark. Specifically, this lab focuses on isolating and breaking down a Domain Name System (DNS) lookup triggered via the command line.

🛠️ Environment & Tools
Packet Analyzer: Wireshark

OS / Terminal: [e.g., Windows Command Prompt / macOS Terminal]

Network Tool: nslookup

🚀 Lab Steps & Walkthrough
1. Generating Traffic (nslookup)
To capture specific DNS traffic, a manual query was initiated using the command-line utility nslookup targeting google.com.

Bash
nslookup google.com
Insert a description of the terminal output here (e.g., the local DNS server used and the resolved IPv4/IPv6 addresses).

📸 Screenshot: Terminal Execution
<img width="1000" alt="image" src="https://github.com/DavidPatrick92/Wireshark_-_Network_Analysis/blob/main/images/Wireshark%20(Nslookup).png">

2. Packet Capture & Filtering in Wireshark
A live packet capture was started on the active network interface.

Once the traffic was generated, the capture was stopped.

The display filter bar was used to isolate only DNS traffic:

Plaintext
dns
📸 Screenshot: Wireshark Main Capture Window
🔍 Deep-Dive Packet Analysis
A. DNS Query (Standard Query)
Packet Number: [e.g., 42]

Source IP: [Your Local IP] ➡️ Destination IP: [Your DNS Server IP]

Protocol: UDP | Source Port: [e.g., 53214] ➡️ Destination Port: 53

Info Summary: Standard query 0x1234 A google.com

Key Details Formatted:
Transaction ID: 0x....

Query Name: google.com

DNS Record Type: A Record (Maps a domain name to an IPv4 address)

📸 Screenshot: DNS Query Packet Details
B. DNS Response (Standard Query Response)
Packet Number: [e.g., 45]

Source IP: [Your DNS Server IP] ➡️ Destination IP: [Your Local IP]

Protocol: UDP | Source Port: 53 ➡️ Destination Port: [e.g., 53214]

Info Summary: Standard query response 0x1234 A google.com

Key Details Formatted:
Answers Section: Contains the resolved IP addresses for google.com.

Time-to-Live (TTL): [e.g., 300 seconds]

📸 Screenshot: DNS Response Packet Details
💡 Key Takeaways & Conceptual Analogy
Think of a DNS A Record like looking up a restaurant's name in a physical phonebook to find its street address.

The Query is you asking: "Where is google.com located?"

The A Record Response is the phonebook returning the exact numerical coordinates: 142.250.XXX.XXX.

Wireshark acts as the security camera recording the exact moment you made the call, verifying that the request and response matched seamlessly using the Transaction ID.
