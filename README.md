# ReconMethology
# 🎯 ReconMethodology

> A professional bug bounty reconnaissance methodology built from real-world hunting experience, automation, and practical attack surface analysis.

![BugBounty](https://img.shields.io/badge/Bug%20Bounty-Recon-red)
![Security](https://img.shields.io/badge/Application-Security-blue)
![Status](https://img.shields.io/badge/Status-Active-success)
![License](https://img.shields.io/badge/License-MIT-green)

---

# 📌 Overview

**ReconMethodology** is a structured reconnaissance methodology designed for **Bug Bounty Hunters, Pentesters, and Security Researchers** to efficiently discover hidden attack surfaces, exposed assets, sensitive endpoints, APIs, misconfigurations, and potential vulnerabilities.

This methodology combines:

- Manual Reconnaissance
- Automated Reconnaissance
- Attack Surface Mapping
- API Enumeration
- JavaScript Analysis
- Content Discovery
- Cloud Asset Discovery
- Vulnerability-Oriented Hunting

The objective is simple:

> **Find more attack surface → Discover overlooked assets → Increase vulnerability findings**

---

# 🧠 Recon Philosophy

In Bug Bounty, vulnerabilities are often hidden behind **good reconnaissance**.

Many hunters focus only on scanning, but professional bug hunters know that:

> **Recon is where real bugs begin.**

This repository focuses on building a **repeatable, scalable, and practical reconnaissance workflow** based on real-world hunting experience.

---

# 🔥 Recon Workflow

```text
Scope Analysis
      ↓
Subdomain Enumeration
      ↓
Live Host Detection
      ↓
Port Scanning
      ↓
Technology Fingerprinting
      ↓
Endpoint Discovery
      ↓
JavaScript Recon
      ↓
Parameter Discovery
      ↓
API Discovery
      ↓
Cloud Asset Enumeration
      ↓
Subdomain Takeover Checks
      ↓
Vulnerability Hunting
```

---

# ⚔️ Methodology

## 1️⃣ Scope Analysis

Before starting reconnaissance:

- Read the program scope carefully
- Understand exclusions
- Identify wildcards
- Review out-of-scope assets
- Analyze acquisition history
- Check ASN ranges
- Search public assets

### Goals
- Avoid wasting time
- Prioritize valuable targets
- Expand attack surface safely

---

## 2️⃣ Subdomain Enumeration

Gather maximum subdomains using passive and active techniques.

### Tools

- Subfinder
- Amass
- Assetfinder
- crt.sh
- Chaos Dataset
- DNSDumpster

### Example Workflow

```bash
subfinder -d target.com -all -silent | tee subdomains.txt

amass enum -passive -d target.com >> subdomains.txt

sort -u subdomains.txt -o subdomains.txt
```

---

## 3️⃣ Live Host Detection

Filter only reachable assets.

### Tools

- httpx

### Example

```bash
cat subdomains.txt | httpx -silent -tech-detect -status-code -title
```

---

## 4️⃣ Port Scanning

Discover exposed services.

### Tools

- Naabu
- Nmap

### Example

```bash
cat alive.txt | naabu -rate 5000 -top-ports 1000
```

---

## 5️⃣ Content Discovery

Find hidden endpoints and admin panels.

### Tools

- ffuf
- dirsearch
- feroxbuster

### Example

```bash
ffuf -u https://target.com/FUZZ \
-w wordlist.txt
```

---

## 6️⃣ JavaScript Recon

Analyze JavaScript files for:

- Secrets
- API endpoints
- Hidden functionality
- Tokens
- Internal paths

### Tools

- Katana
- LinkFinder
- SecretFinder
- JSParser

---

## 7️⃣ Parameter Discovery

Collect hidden parameters.

### Tools

- ParamSpider
- Arjun
- gau
- waybackurls

### Example

```bash
paramspider -d target.com
```

---

## 8️⃣ API Recon

Identify APIs and undocumented endpoints.

### Targets

- Swagger
- GraphQL
- REST APIs
- Mobile APIs

### Checks

- IDOR/BOLA
- Authentication Bypass
- Rate Limits
- Business Logic
- Sensitive Data Exposure

---

## 9️⃣ Cloud Recon

Find exposed storage assets.

### Targets

- S3 Buckets
- Azure Blobs
- GCP Storage

### Techniques

- Google Dorking
- Public Bucket Enumeration
- Cloud Exposure Discovery

---

## 🔟 Subdomain Takeover

Check dangling DNS records.

### Tools

- Subzy

---

## 1️⃣1️⃣ Vulnerability Hunting

After recon, begin focused testing for:

- IDOR
- XSS
- SSRF
- Open Redirect
- Authentication Bypass
- Access Control Issues
- Business Logic Bugs
- Sensitive Data Exposure
- Misconfigurations
- API Vulnerabilities

---

# 🛠️ Tools Used

`httpx` • `Katana` • `ParamSpider` • `Naabu` • `Subfinder` • `Amass` • `Nuclei` • `Subzy` • `gau` • `waybackurls` • `ffuf` • `Burp Suite` • `Nmap` • `Arjun` • `Feroxbuster`

---

# 🎯 Why This Repository?

This repository exists to document a **real-world reconnaissance process** used during:

- Bug Bounty Hunting
- Attack Surface Analysis
- Web Application Security Testing
- API Security Testing
- Pentesting Engagements

The methodology emphasizes:

✅ Efficiency  
✅ Automation  
✅ Repeatability  
✅ Coverage  
✅ High-value asset discovery

---

# 🚀 Future Improvements

- [ ] Add automation scripts
- [ ] Add recon screenshots
- [ ] Add cloud recon section
- [ ] Add API recon checklist
- [ ] Add recon decision tree
- [ ] Add bug bounty case studies

---

# 👨‍💻 Author

**Sherif Maher (0xtrav)**  
Information Security Engineer | Bug Bounty Hunter | SOC Analyst

> *"The better your recon, the better your findings."*

---

⭐ If you find this useful, consider giving it a star.
