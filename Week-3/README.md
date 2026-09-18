
# 🔐 Week 3 - Advanced Cybersecurity Practical

## 📌 Overview

During Week 3 of my Cybersecurity Internship at DG Interns Hub, I performed a practical network security assessment using Kali Linux.

The main focus of this week was network scanning, packet analysis, firewall configuration, and security hardening using tools such as Nmap, Wireshark, and UFW.

---

## 🎯 Objectives

- Perform network discovery using Nmap
- Identify active hosts in the lab network
- Perform port and service scanning
- Capture and analyze network traffic using Wireshark
- Analyze ICMP, DNS, HTTP, and TCP traffic
- Understand TCP SYN behavior
- Configure and enable the UFW firewall
- Block unnecessary ports
- Verify the system after security hardening

---

## 🛠️ Tools Used

- Kali Linux
- Nmap
- Wireshark
- UFW Firewall
- Oracle VirtualBox

---

## 🌐 Network Discovery

I first identified my network configuration using:

`ip a`

My Kali Linux virtual machine was using the IP address:

`10.0.2.15/24`

I then performed host discovery using:

`sudo nmap -sn 10.0.2.0/24`

The scan discovered three active hosts in the virtual lab network.

---

## 🔍 Nmap Port & Service Scanning

I performed a service/version scan using:

`sudo nmap -sV 10.0.2.15`

The host was active, but the 1000 commonly scanned TCP ports were reported as closed.

I also performed a targeted scan for FTP and Telnet:

`sudo nmap -p 21,23 10.0.2.15`

Both ports were reported as closed.

---

## 🦈 Wireshark Packet Analysis

Wireshark was used to capture and analyze network traffic on the `eth0` interface.

### Filters Used

- `icmp`
- `dns`
- `tcp`
- `tcp.flags.syn == 1`
- `tcp.analysis.retransmission`

### Traffic Analyzed

**ICMP:** Observed Echo Request and Echo Reply packets generated through ping testing.

**DNS:** Captured DNS queries and responses while resolving domain names.

**TCP:** Analyzed TCP packets and SYN/SYN-ACK behavior to understand connection establishment.

**HTTP:** Observed HTTP request and response traffic during controlled testing.

---

## 🛡️ Firewall Hardening Using UFW

I checked the firewall status using:

`sudo ufw status verbose`

UFW was initially inactive, so I enabled it:

`sudo ufw enable`

I then added explicit deny rules for Telnet and FTP:

`sudo ufw deny 23/tcp`

`sudo ufw deny 21/tcp`

Finally, I verified the rules using:

`sudo ufw status numbered`

The firewall was active with incoming traffic denied by default.

---

## 🔎 Security Findings

- No listening service was detected on the 1000 commonly scanned TCP ports of the tested Kali VM.
- FTP port 21 and Telnet port 23 were closed during verification.
- UFW was successfully enabled.
- Explicit deny rules were configured for FTP and Telnet.
- ICMP, DNS, HTTP, and TCP traffic were successfully observed and analyzed in Wireshark.

---

## 📚 Key Learnings

During Week 3, I learned how to:

- Discover hosts on a network
- Perform Nmap port and service scans
- Analyze packets using Wireshark
- Understand DNS and ICMP communication
- Observe TCP connection behavior
- Configure Linux firewall rules
- Reduce unnecessary network exposure
- Verify security controls after hardening

---

## 📂 Week 3 Deliverables

- 📄 Week 3 Cybersecurity Assignment Report (PDF)
- 📊 Week 3 Cybersecurity Presentation (PPT)
- 📝 Week 3 README Documentation

---

## ⚠️ Disclaimer

All security testing and network scanning documented in this project was performed in my own authorized virtual lab environment for educational purposes only.

---

## 👨‍💻 Internship

**Organization:** DG Interns Hub  
**Domain:** Cybersecurity  
**Week:** 3  
**Intern ID:** DG/SEPTEMBER/CYBER/171
