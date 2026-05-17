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

### 📁 Screenshot Directory Structure
> [!TIP]
> Before adding your images, create an `images/` folder inside your GitHub repository root. Name your screenshot files cleanly (e.g., `exercise_a_terminal.png`) and drop them there so the paths below link automatically.

---

### 🔹 Exercise A — Capture a DNS Lookup
**Objective:** Generate a manual DNS query using the `nslookup` command-line utility and capture the A-record query and response within Wireshark.

1. Initiated a live capture on the active network interface in Wireshark.
2. Executed a targeted query via the local terminal:
   ```bash
   nslookup google.com
