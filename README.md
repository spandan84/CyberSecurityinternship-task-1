# CyberSecurityInternship-Task-1


## 📌 Task Title:
**Scanning Local Network for Open Ports using Nmap**

---

## 🧠 Objective:
The objective of this task was to perform **network reconnaissance** on the local network to discover open ports and identify potentially exposed services. This enhances understanding of how attackers can probe for vulnerabilities in a networked environment.

---

## 🛠️ Tools & Technologies Used:
- [Nmap](https://nmap.org/) – For network scanning and port discovery
- [Wireshark](https://www.wireshark.org/) *(optional)* – For packet-level traffic inspection
- Terminal (Linux Environment)
- GitHub – For task submission and documentation

---

## Performing a TCP SYN Scan using Nmap

A TCP SYN scan (half-open scan) was chosen due to its stealthy behavior. The scan works by sending a SYN packet and analyzing the response:
- SYN-ACK → Port is open
- RST → Port is closed
- No response or ICMP unreachable → Port is filtered
```bash
nmap -sS 192.168.1.0/24 -oN scan.txt
```

### Optional Packet Capture using Wireshark

Wireshark was used to capture real-time packets during the Nmap scan:

- Started a live capture on the active network interface.
- Re-ran the Nmap scan while capture was running.
- Observed multiple TCP SYN packets being sent from the scanner to devices in the subnet.
- Detected SYN-ACK responses from devices with open ports.
- Used the following display filter in Wireshark to isolate SYN packets:

```wireshark filter
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

---

### 📌 Experimental Observations:

- Devices such as routers and Linux machines were detected.
- SYN scanning was fast and silent (no firewall alerts).
- Open services included web admin pages, SSH, and SMB.

---

### ⚠️ Limitations:

- SYN scan does not work on UDP ports.
- Some firewalls might block or obscure scan results.
- Open ports indicate presence of service but not its security status.

---

### ✅ Conclusion:

This experiment demonstrates how port scanning reveals crucial insights about the network. It mimics the reconnaissance phase of an attacker and highlights the need to secure unnecessary open ports and monitor services continuously.


---

## 🧠 Concepts Learned:

- **Port Scanning**  
  Learned how to scan a range of IPs to detect active devices and open ports using Nmap.

- **TCP SYN Scan Technique**  
  Understood the working of stealthy TCP SYN scanning and how it identifies open ports without completing the TCP handshake.

- **IP Addressing and Subnet Scanning**  
  Gained experience working with CIDR notations like `/24` to scan entire subnets effectively.

- **Packet Inspection using Wireshark**  
  Analyzed real-time traffic and understood how SYN packets and responses reveal port states.

- **Network Security Awareness**  
  Understood the implications of exposed services and the importance of closing or filtering unused ports.

---



## 🙋‍♂️ Author:

**Name:** Spandan Jana
**Role:** Cybersecurity Intern @The ELevate Labs

**Task Date:** 23rd June 2025

---
