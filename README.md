# cyber-internship-task3 
# 🔒 Task 3 — Vulnerability Scan on My PC  
**Elevate Labs — Cyber Security Internship**

---

## 📌 Objective
Perform a vulnerability assessment on my personal machine using Nessus Essentials, identify risks, analyze severity levels, and document remediation steps. This task demonstrates practical exposure to automated security scanning.

---

## 🛠 Tools Used
- **Nessus Essentials (Free Edition)**
- Windows 10
- Target System IP: `192.168.1.43`
- Scan Policy: **Basic Network Scan**

---

## 🚀 Steps Performed
1. Installed and activated Nessus Essentials.
2. Created a new **Basic Network Scan** with the target set to `192.168.1.43`.
3. Launched a full vulnerability scan (10 minutes as per Nessus report).
4. Reviewed severity distribution and analyzed key findings.
5. Exported the HTML report.
6. Documented the results with screenshots and detailed explanations.

---

## 📊 Scan Summary
Nessus detected the following vulnerabilities:

| Severity  | Count |
|-----------|-------|
| Critical  | 0 |
| High      | 0 |
| Medium    | 2 |
| Low       | 0 |
| Info      | 22 |
| **Total** | **24** |

A large percentage of findings were informational, which is expected in an unauthenticated scan. Two medium-severity vulnerabilities require attention.

---

## 🔍 Detailed Vulnerability Analysis

### 1️⃣ **SMB Signing Not Required**
**Severity:** Medium  
**Nessus Plugin ID:** 57608  

**Description:**  
The host’s SMB server (port 445) does not enforce SMB message signing. Without signing, an attacker on the local network may perform **man-in-the-middle (MITM)** attacks by modifying SMB traffic.

**Risk:**  
- Session hijacking  
- Manipulation of SMB traffic  
- Potential credential exposure  

**Solution:**  
Enable SMB signing on Windows:  
- Group Policy → Local Computer Policy  
- Computer Configuration → Windows Settings → Security Settings → Local Policies → Security Options  
- Set **"Microsoft network server: Digitally sign communications (always)"** to **Enabled**

---

### 2️⃣ **SSL Certificate Cannot Be Trusted**
**Severity:** Medium  
**Nessus Plugin ID:** 51192  
**Affected Port:** 8834 (Nessus local web interface)

**Description:**  
The SSL certificate presented by the host is **self-signed**, not issued by a trusted Certificate Authority. This is common for local security tools running on HTTPS.

**Risk:**  
- Users cannot validate authenticity  
- Possible spoofing if intercepted  
- MITM attacks (only realistic on public-facing services)

**Solution:**  
For production systems, install a certificate signed by a recognized CA.  
For local Nessus installations, this warning is expected and low risk.

---

## 🧠 Informational Findings (Summary)
Nessus reported 22 informational findings, including:
- TLS/SSL version detection  
- OS identification  
- Netstat enumeration  
- Service detection  
- Additional DNS hostnames  
- SMB/HTTP/TLS protocol information  

These findings help build a profile of the system but do not indicate direct vulnerabilities.

---

## 📁 Repository Contents

├── README.md

└── screenshots/

├── dashboard.png

├── scan-dashboard.png

├── scan-details-1.png

├── scan-details-2.png

├── smb-vulnerability.png

└── ssl-vulnerability.png

---

## 🛡 Recommendations
- Enable SMB signing for improved LAN security.
- Use valid CA-signed certificates for any public-facing HTTPS services.
- Keep Windows OS and installed software updated.
- Perform periodic vulnerability scans for early detection.
- Strengthen authentication and disable unnecessary services.

---

## 📝 Conclusion
This task provided hands-on experience with **vulnerability scanning, risk interpretation, CVSS severity understanding, and structured documentation**. Nessus Essentials successfully identified medium-severity issues and generated valuable insights for improving system security.

The experience reflects real-world vulnerability assessment workflows used in professional security operations.

