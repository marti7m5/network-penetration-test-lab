# Network Penetration Testing Lab
Hands-on network penetration testing lab simulating real-world internal security assessment with Nmap, Nikto, and Gobuster.

## Objective
Conduct a simulated internal network penetration test to identify vulnerabilities, misconfigurations, and attack paths.

## Tools Used
- Nmap
- Nikto
- Gobuster
- Netcat

## Methodology
1. Network Discovery
2. Port Scanning
3. Service Enumeration
4. Vulnerability Scanning
5. Directory Enumeration
6. Manual Validation

## Key Findings
- Open ports and exposed services
- Missing HTTP security headers
- Accessible file shares
- Service version disclosure

## Risk Analysis

### 1. Exposed SSH Service (Port 22)

**Risk:** The SSH service is publicly accessible and may allow unauthorized access if weak credentials or outdated configurations are present.

**Impact:** An attacker could perform brute-force attacks or exploit vulnerabilities to gain initial access to the system, potentially leading to full system compromise.

**Likelihood:** Moderate. SSH is a common attack target, and automated tools frequently scan for exposed services.

---

### 2. Missing HTTP Security Headers

**Risk:** The web server does not implement key security headers such as X-Frame-Options and Content-Security-Policy.

**Impact:** This could allow attacks such as clickjacking or cross-site scripting (XSS), potentially compromising user sessions or sensitive data.

**Likelihood:** High. Misconfigured headers are common and easily exploitable.

---

### 3. Service Version Disclosure

**Risk:** The server reveals software version information (e.g., nginx version), which can be used by attackers to identify known vulnerabilities.

**Impact:** Attackers can target specific exploits associated with the disclosed version, increasing the likelihood of successful compromise.

**Likelihood:** High. Automated scanners actively look for version disclosures.

---

### 4. Accessible File Shares (SMB/NFS)

**Risk:** File-sharing services are accessible and may allow unauthorized users to read or modify sensitive data.

**Impact:** Could lead to data leakage, credential exposure, or lateral movement within the network.

**Likelihood:** Moderate to High depending on access controls.

## MITRE ATT&CK Mapping

The following techniques were observed or simulated during the assessment:

### T1046 – Network Service Discovery
- Used Nmap to identify active hosts and open ports within the network.

### T1082 – System Information Discovery
- Service enumeration revealed system details such as running services and configurations.

### T1595 – Active Scanning
- Conducted automated scanning to identify vulnerabilities and exposed services.

### T1190 – Exploit Public-Facing Application
- Web server testing (Nikto, Gobuster) identified potential vulnerabilities in exposed web applications.

### T1083 – File and Directory Discovery
- Gobuster was used to enumerate hidden directories and files on the web server.

### T1021 – Remote Services
- SSH and SMB services could be leveraged for remote access if credentials are compromised.
## Remediation Recommendations
- Patch management
- Service hardening
- Network segmentation
