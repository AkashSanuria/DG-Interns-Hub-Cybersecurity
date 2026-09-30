🔐 DG Interns Hub - Cybersecurity Internship
📘 Week 4: Basic Network Setup & Initial Security Testing
Intern: Akash Sanuria
Intern ID: DG/SEPTEMBER/CYBER/171
Organization: DG Interns Hub
Domain: Cybersecurity
Week: 4
📌 Project Overview
In Week 4, I created a small virtual cybersecurity lab using Kali
Linux and Ubuntu Linux.
The objective was to understand basic network setup, configure a web
service, perform network scanning with Nmap, and analyze network
traffic using Wireshark.
All testing was performed inside an authorized VirtualBox lab
environment.
🎯 Objectives
- Create a small lab network using VirtualBox.
- Connect Kali Linux and Ubuntu on the same subnet.
- Verify communication between both virtual machines.
- Install and configure Apache2 on the Ubuntu target.
- Perform service and version detection using Nmap.
- Capture and analyze ICMP, DNS, and HTTP traffic using Wireshark.
- Save scan evidence and document the practical workflow.
🛠️ Tools Used
  Tool                Purpose
  Oracle VirtualBox   Virtual machine and network lab environment
  Kali Linux          Attacker / testing machine
  Ubuntu Linux        Target machine
  Apache2             HTTP web service
  Nmap                Port and service discovery
  Wireshark           Packet capture and traffic analysis
🌐 Lab Environment
  Machine        Role                         Final IP Address
  Kali Linux     Attacker / Testing Machine   10.0.2.15
  Ubuntu Linux   Target Machine               10.0.2.5
- Network: 10.0.2.0/24
- Network Type: VirtualBox NAT Network
- DHCP: Enabled
Note: DHCP reassigned the VM IP addresses during the practical, so the
final addresses were rechecked before scanning.

✅ Task 1 - Basic Network Setup
A NAT Network named NatNetwork was created in VirtualBox with the
IPv4 prefix 10.0.2.0/24 and DHCP enabled.
Both Kali Linux and Ubuntu Linux were connected to the same virtual
network.
Connectivity was verified using:
ping -c 4 10.0.2.5
Result
- 4 packets transmitted
- 4 packets received
- 0% packet loss
- Kali and Ubuntu successfully communicated with each other
🌐 Task 2 - Apache Web Server
Apache2 was installed on the Ubuntu target machine.
sudo apt install apache2 -y
The Apache service was verified using:
sudo systemctl status apache2
Result
Apache2 was successfully verified as:
Active: active (running)
The Apache default page was accessed from Kali using:
http://10.0.2.5
This confirmed that the HTTP service was reachable over the lab network.
🔍 Task 3 - Nmap Network Scanning
Service and version detection was performed from Kali against the Ubuntu
target.
nmap -sV 10.0.2.5
Nmap Findings
  Port       State   Service   Version
  80/tcp   Open    HTTP      Apache httpd 2.4.58 (Ubuntu)
The final scan was saved using:
nmap -sV 10.0.2.5 -oN week4_final_nmap.txt
The saved output was verified using:
cat week4_final_nmap.txt
Result
Nmap successfully identified the open HTTP service running on TCP port
80.
📡 Task 4 - Wireshark Traffic Analysis
Wireshark was used on Kali Linux using the eth0 interface.
Three protocols were analyzed:
1️⃣ ICMP Analysis
Display filter:
icmp
A ping from Kali 10.0.2.15 to Ubuntu 10.0.2.5 generated:
- ICMP Echo Requests
- ICMP Echo Replies
- 0% packet loss
2️⃣ DNS Analysis
DNS traffic was generated using:
nslookup google.com
Display filter:
dns
Wireshark showed DNS queries and responses while the terminal confirmed
successful domain-name resolution.
3️⃣ HTTP Analysis
The Apache page was opened from Kali while Wireshark captured the
traffic.
Display filter:
http && ip.addr == 10.0.2.5
Observed
- HTTP GET requests from Kali
- HTTP responses from Ubuntu
- Apache2 default page successfully loaded
- End-to-end web communication confirmed
🔄 Complete Practical Workflow
VirtualBox Network Setup
        ↓
Kali Linux + Ubuntu Linux
        ↓
Connectivity Testing
        ↓
Apache2 Web Server Setup
        ↓
Nmap Service Scan
        ↓
Wireshark Packet Capture
        ↓
ICMP + DNS + HTTP Analysis
⚠️ Challenges Faced
During the Week 4 practical, I faced:
- DNS resolution failure
- DHCP IP address changes after VM restart
- Destination Host Unreachable error
- Apache service configuration issue
- HTTP vs HTTPS connection confusion
🔧 Troubleshooting
I solved these challenges by:
- Checking the current IP addresses of both virtual machines.
- Confirming both VMs were connected to the same VirtualBox NAT
  Network.
- Testing communication using ping.
- Restoring DNS resolution before installing packages.
- Rechecking DHCP-assigned IP addresses after restarting the VMs.
- Installing and verifying Apache2 on the active Ubuntu system.
- Using HTTP on TCP port 80 for the configured Apache web server.
📚 Key Learnings
This week helped me improve my understanding of:
- VirtualBox networking
- IP addressing and DHCP
- Network connectivity testing
- Linux web server configuration
- Nmap port and service scanning
- Nmap output saving
- Wireshark packet analysis
- ICMP traffic
- DNS traffic
- HTTP traffic
- Basic network troubleshooting
🎯 Conclusion
Week 4 provided practical experience with a complete basic network
security workflow.
I successfully completed:
Network Setup → Connectivity Testing → Apache2 Configuration → Nmap
Scanning → Wireshark Traffic Analysis
This practical strengthened my foundation in Networking, Network
Security, and SOC Analysis.
