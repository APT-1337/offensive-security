# 🕵️‍♂️ Web Information Gathering 

## 📘 Introduction

The **Information Gathering** phase is the first and one of the most critical steps in web application penetration testing. The goal is to collect as much information as possible about the target — without (in passive mode) or with (in active mode) interacting with it directly. This information helps to identify technologies, entry points, and potential vulnerabilities.

---

## 🔹 Types of Information Gathering

### 1. Passive Information Gathering

Passive reconnaissance involves collecting data without directly interacting with the target. It's stealthy and useful for avoiding detection.

#### 🔧 Tools and Techniques:

- **Whois**

  - 🔍 Retrieves domain registration information, including registrant, contact, and name server details.
  - 🧪 Example:
    ```bash
    whois example.com
    ```

- **DNS Enumeration**

  - ⛓️ Retrieves DNS records such as A, MX, NS, TXT.
  - 🧪 Examples:
    ```bash
    nslookup example.com
    dig example.com any
    host -a example.com
    ```

- **Google Dorking**

  - 🔎 Leverages advanced Google search queries to discover sensitive information.
  - 🧪 Examples:
    ```
    site:example.com filetype:pdf
    inurl:admin site:example.com
    intitle:index.of site:example.com
    ```

- **Wayback Machine**

  - 🕰️ Used to view historical snapshots of websites: [https://archive.org/web](https://archive.org/web)

- **Shodan / Censys**

  - 🌐 Internet search engines that reveal information about exposed services/devices.
  - 🧪 Shodan example:
    ```
    hostname:"example.com"
    ```

- **theHarvester**

  - 🧲 Gathers emails, subdomains, hosts, and usernames from public sources.
  - 🧪 Example:
    ```bash
    theHarvester -d example.com -b google
    ```

- **Recon-ng**

  - 🛠️ A modular OSINT framework for automated reconnaissance.
  - 🧪 Sample workflow:
    ```bash
    recon-ng
    > marketplace install all
    > use domains-contacts/whois_pocs
    > run
    ```

---

### 2. Active Information Gathering

Active recon involves direct interaction with the target — sending requests, scanning ports, and probing services. It can be detected by intrusion detection systems (IDS).

#### 🔧 Tools and Techniques:

- **Nmap**

  - 🌐 Performs port scanning and service/version detection.
  - 🧪 Example:
    ```bash
    nmap -sV -T4 -Pn example.com
    ```

- **WhatWeb / Wappalyzer**

  - 🧠 Identifies web technologies such as server software, CMS, JavaScript frameworks, etc.
  - 🧪 Example:
    ```bash
    whatweb example.com
    ```

- **Gobuster / Dirb / FFUF**

  - 📂 Enumerates hidden directories and files by brute-forcing paths.
  - 🧪 Example:
    ```bash
    gobuster dir -u https://example.com -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
    ```

- **SSL/TLS Scanning (testssl.sh / sslscan)**

  - 🔐 Detects SSL/TLS versions, supported ciphers, certificate issues.
  - 🧪 Example:
    ```bash
    testssl.sh example.com
    ```

- **WAF Detection (wafw00f)**

  - 🛡️ Identifies Web Application Firewalls protecting the target.
  - 🧪 Example:
    ```bash
    wafw00f https://example.com
    ```

---

## 📌 Key Information to Collect

- Subdomains and virtual hosts
- Web server technologies (e.g., Apache, Nginx)
- Backend languages (PHP, Python, ASP.NET, etc.)
- Frontend frameworks (e.g., React, Angular)
- Login/admin panels
- Public APIs
- Hidden files or folders (e.g., `.git`, `robots.txt`, `sitemap.xml`)
- HTTP headers and status codes
- SSL certificates and security settings

---

## 🧰 Useful Tools Summary

| Tool            | Purpose                          |
| --------------- | -------------------------------- |
| `whois`         | Domain registration info         |
| `nslookup/dig`  | DNS record retrieval             |
| `nmap`          | Port and service enumeration     |
| `gobuster/ffuf` | Directory/file brute-forcing     |
| `whatweb`       | Detect web technologies          |
| `theHarvester`  | OSINT: Emails, subdomains, names |
| `recon-ng`      | Automated OSINT framework        |
| `wafw00f`       | Detect web firewalls             |

---

