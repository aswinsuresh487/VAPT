# 🛡️ Cybersecurity Professional | VAPT & Penetration Testing

**Aswin Suresh** | Certified Specialist in Cyber Security Analyst

## 👋 About Me

Aspiring cybersecurity professional specializing in **Vulnerability Assessment and Penetration Testing (VAPT)**. I conduct comprehensive security assessments, identify critical vulnerabilities, and deliver actionable remediation strategies. With hands-on experience in web application security, network infrastructure testing, and Linux privilege escalation, I'm committed to strengthening digital security.

---

## 🎯 Core Expertise

| Area | Skills |
|---|---|
| **Web Application Security** | SQL Injection, XSS, File Upload Exploits, Authentication Bypass |
| **Network Security** | Port Scanning, Service Enumeration, Banner Grabbing, Infrastructure Mapping |
| **Penetration Testing** | Exploitation, Privilege Escalation, PoC Validation, Attack Chain Development |
| **Vulnerability Assessment** | CVSS Scoring, Risk Prioritization, EOL Software Detection, Compliance Analysis |
| **Infrastructure Testing** | Linux Hardening, SSH/FTP Security, LDAP/NFS Enumeration, Database Security |

---

## 🛠️ Technical Toolkit

**Security Testing Tools**
- Nmap, Nessus, Nikto, Gobuster, WhatWeb
- Burp Suite, sqlmap, Hydra, Slowloris
- LinPEAS, Linux Exploit Suggester
- Metasploit Framework

**Reconnaissance & Forensics**
- Shodan, Censys, VirusTotal, IPVoid
- Wireshark, NetCat (nc)
- DNS Tools: dig, dnsrecon, ldapsearch

**Infrastructure**
- Kali Linux, Ubuntu, Bash/Shell Scripting
- Python, SQL
- Virtual Environments: VirtualBox, Genymotion

---

## 📋 Projects & Assessments

### **Phase 1: Literature Survey on VAPT**
**Date:** October 5, 2025
**Focus:** Comprehensive research on VAPT methodologies across diverse environments

**Key Contributions:**
- Analyzed VAPT frameworks vs. Cyber Attack Lifecycle
- Documented implementation strategies for Network, Web, Cloud, and IoT environments
- Identified current trends: AI-driven automation, cloud-native security, edge computing
- Comparative analysis of VAPT benefits and limitations

**Deliverables:** Research report with 15+ academic references and industry frameworks

---

### **Phase 2: Reconnaissance Assessment**
**Target:** 139.59.2.14 (Ubuntu Server on DigitalOcean)
**Date:** October 7-11, 2025
**Team:** Collaborative assessment with Devika G, Vaishnav K.R

**Attack Surface Identified:**
- **14 Open Services:** FTP, SSH, DNS, HTTP (3 instances), LDAP, NFS, MariaDB, RPC
- **46 Active Hosts** in same subnet (heightened risk environment)
- **Critical Exposure:** phpMyAdmin interface, outdated Apache/PHP, exposed database

**Reconnaissance Techniques:**
```bash
# OSINT & Passive Intelligence
- WHOIS/DNS reverse lookup
- Certificate transparency analysis
- Network range enumeration

# Active Discovery
- Nmap comprehensive port scanning (1-65535)
- Banner grabbing & service fingerprinting
- Web application directory discovery
- Infrastructure role identification
```

**Key Findings:**
- Apache 2.4.38 & 2.4.41 with known CVEs
- PHP 5.6.40 (End-of-Life since January 2017)
- MariaDB 10.3.23 with known advisories
- Multiple web servers on non-standard ports
- Unprotected LDAP directory services

**Risk Level:** 🔴 **CRITICAL** - Multiple exploitation vectors available

---

### **Phase 3: Vulnerability Assessment Report**
**Target:** 139.59.2.14
**Date:** October 11, 2025
**Scope:** 9 open TCP services evaluated with automated and manual techniques

**Vulnerability Breakdown:**
```
┌─────────────────────────────────────┐
│ 21 Total Vulnerabilities Identified │
├─────────────────────────────────────┤
│ 🔴 Critical:    7 (33%)             │
│ 🟠 High:        3 (14%)             │
│ 🟡 Medium:      6 (29%)             │
│ 🔵 Low:         5 (24%)             │
└─────────────────────────────────────┘
```

**Critical Vulnerabilities (CVSS 8.0+):**
1. **PHP 5.6.40 RCE** - CVE-2019-11043 (CVSS 9.8)
2. **EOL PHP** - No security patches since 2018 (CVSS 10.0)
3. **Apache 2.4.38 Multiple RCE/DoS** - CVE-2021-39275, CVE-2021-34798 (CVSS 9.8)
4. **OpenSSL 1.0.2q Buffer Over-read** - CVE-2024-5535 (CVSS 9.1)
5. **HTTP TRACE Method Enabled** - XST Attack (CVSS 8.0)
6. **phpMyAdmin Directory Exposure** - Unauthenticated admin access (CVSS 8.5)
7. **Directory Indexing Enabled** - tmp & icons exposed (CVSS 7.5)

**High/Medium Issues:**
- Missing security headers (X-Frame-Options, X-Content-Type-Options)
- Enabled mod_negotiation/MultiViews
- FTP banner version disclosure
- Anonymous LDAP bind allowed

**Remediation Roadmap:**
- **Immediate (0-7 days):** Upgrade PHP 8.1+, Apache 2.4.54+, OpenSSL 3.0.7, disable TRACE
- **Short-term (7-30 days):** Implement security headers, restrict phpMyAdmin, disable indexing
- **Medium-term (30-90 days):** Deploy WAF, automated patch cycles, comprehensive monitoring

---

### **Phase 4: Penetration Testing & Exploitation**
**Target:** 128.199.16.171 (ICTAK Vulnerable Web Application)
**Date:** October 13, 2025
**Team Lead:** Aswin Suresh | Supporting: Devika G, Vaishnav K.R

**Objectives Achieved:**
✅ Identified and validated security weaknesses
✅ Demonstrated real-world attack scenarios
✅ Provided actionable remediation guidance

**Web Application Vulnerabilities (7 Total)**

#### **🔴 CRITICAL - SQL Injection**
- **Location:** Login form, blog search parameters
- **Impact:** Authentication bypass, full database extraction
- **PoC:** `admin' OR '1'='1' --`
- **Payload Validation:** Successfully dumped user table via sqlmap

#### **🔴 CRITICAL - Stored XSS**
- **Location:** Comments section, blog entries
- **Impact:** Persistent JavaScript execution, admin compromise
- **PoC:** `<img src=x onerror=alert(1337)>`
- **Result:** Alert box triggered for all users viewing the comment

#### **🔴 CRITICAL - Insecure File Upload**
- **Location:** Blog image upload endpoint
- **Bypass Technique:** Double-extension (shell.php.jpg)
- **Impact:** PHP shell execution and server compromise
- **PoC:** Successfully uploaded executable PHP file

#### **🟠 HIGH - Weak Authentication**
- **Issue:** No strong password enforcement
- **Risk:** Default credentials accepted (e.g., "admin:admin")
- **Finding:** User creation allows weak/common passwords

#### **🔵 MEDIUM - User Registration Issues**
- **Problem:** Insufficient role-based access control
- **Finding:** Any user can assign administrator privileges

#### **🔴 CRITICAL - Privilege Escalation (Infrastructure)**
- **CVE-2021-3156 (Baron Samedit):** Sudo exploit via malloc heap overflow
- **CVE-2022-0847 (DirtyPipe):** Arbitrary file write via pipe buffer

---

## 📊 Assessment Summary

| Metric | Phase 2 | Phase 3 | Phase 4 |
|---|---|---|---|
| **Target** | 139.59.2.14 | 139.59.2.14 | 128.199.16.171 |
| **Type** | Reconnaissance | Vuln. Assessment | Penetration Test |
| **Findings** | 14 open services | 21 vulnerabilities | 7 vulnerabilities |
| **Critical Issues** | N/A | 7 critical | 3 critical |
| **PoC Validated** | No | Partial | Full |

---

## 🔐 Methodologies Applied

**VAPT Framework:**
1. **Pre-Engagement** - Authorization, scope definition, tool selection
2. **Reconnaissance** - Passive & active information gathering
3. **Vulnerability Analysis** - Automated scanning + manual verification
4. **Exploitation** - Controlled attacks, PoC validation
5. **Reporting** - Risk scoring, remediation roadmap, business impact

**Standards & Best Practices:**
- OWASP Testing Guide v4
- PTES (Penetration Testing Execution Standard)
- NIST Cybersecurity Framework
- CVSS v3.1 Risk Scoring

---

## 📈 Key Achievements

✅ **Identified 35+ unique vulnerabilities** across three targets
✅ **Demonstrated 5 critical attack chains** (SQL injection → RCE, XSS persistence, privilege escalation)
✅ **Validated PoCs** with full evidence documentation (screenshots, logs, packet captures)
✅ **Generated enterprise-grade reports** with CVSS scores and remediation timelines
✅ **Collaborated effectively** in team-based security assessments
