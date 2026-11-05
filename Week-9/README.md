# 🛡️ Week 9 – SOC Introduction & Snort IDS Setup

### Cybersecurity Internship | DG Interns Hub

**Intern Name:** Akash Sanuria  
**Intern ID:** DG/SEPTEMBER/CYBER/171  
**Internship:** Cybersecurity Internship  
**Week:** 9  
**Module:** Security Operations Center (SOC)  
**Status:** ✅ Completed

---

## 🎯 Project Objective

The objective of this project was to understand Security Operations Center (SOC) fundamentals and implement a basic network monitoring environment using Ubuntu Linux and Snort IDS.

The project focused on detecting ICMP and HTTP network traffic through custom Snort rules and analyzing real-time security alerts.

## 📚 Task 1 – SOC Fundamentals

Studied the following concepts:

- Security Operations Center (SOC) and its responsibilities
- L1, L2 and L3 SOC analyst roles
- Security Information and Event Management (SIEM)
- Intrusion Detection System (IDS)
- Intrusion Prevention System (IPS)
- Network traffic monitoring and alert analysis

## 💻 Task 2 – Environment Setup

Configured a virtual cybersecurity monitoring environment using Oracle VirtualBox.

**Environment Details:**

| Component | Configuration |
|---|---|
| Virtualization | Oracle VirtualBox |
| Operating System | Ubuntu 24.04.5 LTS |
| IDS Tool | Snort 2.9.20 |
| Network Interface | enp0s3 |
| HOME_NET | 10.0.2.0/24 |
| Hostname | soc-server |

**Basic Configuration Commands:**

```bash
sudo apt update && sudo apt upgrade -y
sudo hostnamectl set-hostname soc-server
ip -br addr
ping -c 4 8.8.8.8
```

## 🛡️ Task 3 – Snort IDS Installation

Installed and verified Snort IDS on Ubuntu Linux.

```bash
sudo apt install snort -y
snort -V
```

Configured the Snort home network in `/etc/snort/snort.conf`:

```text
ipvar HOME_NET 10.0.2.0/24
```

Validated the configuration:

```bash
sudo snort -T -c /etc/snort/snort.conf -i enp0s3
```

**Result:** Snort successfully validated the configuration.

## ⚙️ Task 4 – Custom Detection Rules

Created two custom Snort rules in:

`/etc/snort/rules/local.rules`

**Rule 1 – ICMP Ping Detection**

```text
alert icmp any any -> any any (msg:"SOC ICMP Ping Detected"; sid:1000001; rev:1;)
```

**Rule 2 – HTTP Traffic Detection**

```text
alert tcp any any -> any 80 (msg:"SOC HTTP Traffic Detected"; sid:1000002; rev:2;)
```

The ICMP rule detects ICMP traffic, while the HTTP rule detects TCP traffic directed to port 80.

## 🔍 Task 5 – Real-Time Traffic Monitoring

Started Snort in live monitoring mode:

```bash
sudo snort -A console -q -c /etc/snort/snort.conf -i enp0s3
```

**ICMP Testing**

```bash
ping -c 4 8.8.8.8
```

Successfully generated ICMP alerts:

```text
[1:1000001:1] SOC ICMP Ping Detected
```

**HTTP Testing**

```bash
curl -4 -v http://example.com/
```

Successfully generated HTTP detection alerts:

```text
[1:1000002:2] SOC HTTP Traffic Detected
```

## 📊 Project Results

| Test | Result |
|---|---|
| Ubuntu Environment Setup | ✅ Completed |
| Snort IDS Installation | ✅ Successful |
| Snort Configuration Validation | ✅ Passed |
| Custom Detection Rules | ✅ Configured |
| ICMP Traffic Detection | ✅ Verified |
| HTTP Traffic Detection | ✅ Verified |
| Real-Time Alert Monitoring | ✅ Successful |

## 🔄 SOC Monitoring Workflow

```text
Network Traffic Generation
          |
          v
Network Interface (enp0s3)
          |
          v
Snort IDS Packet Inspection
          |
          v
Custom Detection Rules
          |
          v
ICMP / HTTP Rule Match
          |
          v
Security Alert Generated
          |
          v
SOC Analyst Investigation
```

## 🧠 Challenges Faced

During this project, I faced several challenges:

- Permission errors while accessing Snort configuration files
- Configuring HOME_NET correctly
- Duplicate Snort rule warnings
- Terminal processes becoming suspended
- HTTP detection alerts not appearing initially

## 🛠️ Solutions Implemented

- Used `sudo` to resolve permission issues.
- Updated the HOME_NET configuration.
- Validated Snort configuration using test mode.
- Checked custom rules and their inclusion in `snort.conf`.
- Troubleshot suspended Snort processes.
- Simplified the HTTP detection rule and successfully verified traffic alerts.

## 📖 Key Learnings

Through this project, I gained hands-on experience in:

- SOC operations and network security monitoring
- Snort IDS installation and configuration
- Custom intrusion detection rule creation
- ICMP and HTTP packet analysis
- Real-time alert generation
- Linux troubleshooting and network diagnostics

## 🏁 Conclusion

The Week 9 project successfully demonstrated basic SOC monitoring using Snort IDS.

Both ICMP and HTTP traffic were detected through custom Snort rules, providing practical experience in network intrusion detection and security event monitoring.

This project strengthened my understanding of SOC workflows, blue-team operations and security alert analysis.

---

**DG Interns Hub | Cybersecurity Internship | Week 9**

**Developed by:** Akash Sanuria
