# 🔐 Week 5 - VAPT Tools Practical Learning

## 📌 Objective

The objective of Week 5 was to understand the basics of
Vulnerability Assessment and Penetration Testing (VAPT) through
practical hands-on activities in an authorized environment.

## 🛠️ Tools Used

- Nmap
- Nikto
- Burp Suite Community Edition
- cURL
- Netcat
- Kali Linux

## 🔎 Task 1 - Nmap Network Scanning

The following scans were performed on the authorized test target:

- `nmap -sS`
- `nmap -sV`
- `nmap -A`

### Learning

I learned how to:

- Identify port states
- Perform service/version detection
- Understand filtered ports
- Interpret Nmap scan results
- Understand the limitations of OS detection

## 🌐 Task 2 - Nikto Web Scanning

Nikto was configured and executed against the authorized test target.

During testing, the target HTTP service was not reachable from the
current network path.

Connectivity was verified using:

- cURL
- Netcat

The connectivity limitation was documented instead of reporting
unverified vulnerability results.

## 🕵️ Task 3 - Burp Suite

Burp Suite Community Edition was configured as an intercepting proxy.

Three HTTP requests were successfully captured:

- `GET /`
- `GET /login.php`
- `GET /artists.php`

I analyzed HTTP request information including:

- Host
- User-Agent
- Accept
- Accept-Encoding
- Connection headers

## 🔍 Key Observations

1. Nmap reported the scanned TCP ports as filtered/no-response.
2. The target HTTP service was unavailable during the Nikto scan.
3. Burp Suite successfully intercepted and displayed HTTP request
   paths and headers.

## 🎯 Key Learning

This week helped me understand that VAPT is not only about running
security tools. Results must be analyzed, validated, and documented
correctly before reporting a security vulnerability.

## ⚠️ Ethical Testing

All security testing was performed only against the authorized
internship test environment.

No unauthorized website or system was tested.

---

**Submitted By:** Akash Sanuria  
**Intern ID:** DG/SEPTEMBER/CYBER/171  
**Internship:** Cybersecurity Internship  
**Week:** Week 5
