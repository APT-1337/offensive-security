# 🧠 OSINT: A Comprehensive Guide to Corporate Reconnaissance

> **A complete reference guide to documenting and executing the OSINT (Open-Source Intelligence) phase during penetration tests or red team operations, based on HTB - OSINT Corporate Recon methodology.**

---

## 📘 Overview

### What is OSINT?

* OSINT (Open-Source Intelligence): Gathering information from public and open sources without direct or active interaction with the target.
* Includes: media, internet, documents, social networks, search engines, and more.

### Importance of OSINT

* Enables you to:

  * Find technical vulnerabilities.
  * Gather credentials.
  * Craft effective social engineering attacks.

### Ethical and Legal Guidelines

| **Activity**                           | **Considered OSINT?** | **Legal?** |
| -------------------------------------- | --------------------- | ---------- |
| Searching for employees on LinkedIn    | ✅                     | ✅          |
| Browsing the company website           | ✅                     | ✅          |
| Brute-forcing subdomains               | ❌                     | ❌          |
| Analyzing SSL certificates with crt.sh | ✅                     | ✅          |

---

## 🧱 Core Elements

| **Element**         | **Description**                                      |
| ------------------- | ---------------------------------------------------- |
| Company Information | Structure, location, services, employees, reputation |
| Infrastructure      | Domains, network, certificates, service providers    |
| Leaks               | Data breaches, leaked information, archived files    |

---

## 🔁 OSINT Cycle

1. Identify the company and the objective.
2. Gather general information (website, social media, resumes, services).
3. Perform search engine queries.
4. Explore forums and repositories.
5. Use newly found info to start another cycle.
6. Document everything (results + method).

> **Structure:** Core Elements ⇨ Sources ⇨ Documentation ⇨ Repeat Cycle

---

## 🧰 Tools & Resources

### 🔎 Information Gathering Tools

* `crt.sh`: SSL certificates.
* `CTFR`: Subdomain enumeration.
* `theHarvester`: Emails and domains.
* `h8mail`: Check breached emails.
* `Shodan`: Search for exposed services.
* `IP2Provider`: Identify ISP from IP.
* `ExifTool`: Extract metadata from files.
* `Hunter.io`: Discover email patterns.
* `Emailrep.io`: Check email reputation.
* `RocketReach`: Look up executives and contact info.
* `html2text`: Convert HTML pages to text.
* `jq`: Parse JSON.
* `csvtojson`: Convert CSV to JSON.

### 🧭 Platforms and Resources

#### 🌐 Official Websites

* [Google Maps](https://www.google.com/maps/)
* [Earth](https://earth.google.com)
* [ShowMyStreet](https://showmystreet.com)
* [Monster](https://www.monster.com/)
* [Indeed](https://indeed.com)
* [Glassdoor](https://www.glassdoor.de)
* [TrustPilot](https://www.trustpilot.com/)

#### 📡 Domain Info

* [crt.sh](https://crt.sh/)
* [CTFR](https://github.com/UnaPibaGeek/ctfr)
* [certificate.transparency.dev](https://certificate.transparency.dev)
* [dnsdumpster](https://dnsdumpster.com)
* [ICANN Lookup](https://lookup.icann.org/)
* [MXToolbox](https://mxtoolbox.com/SuperTool.aspx)
* [ARIN Whois](https://www.arin.net/resources/registry/whois/rws/cli/)
* [BuiltWith](https://builtwith.com/)
* [Grayhat Buckets](https://buckets.grayhatwarfare.com/)

#### 📁 Files and Leaks

* [VirusTotal](https://www.virustotal.com/gui/)
* [Pastebin](https://pastebin.com/)
* [Archive.org](https://archive.org/)
* [archive.fo](https://archive.fo/)
* [HaveIBeenPwned](https://haveibeenpwned.com/)

#### 🌐 Social Media

* [LinkedIn](https://www.linkedin.com/)
* [Twitter](https://twitter.com)
* [Facebook](https://www.facebook.com/)
* [Instagram](https://www.instagram.com/)
* [YouTube](https://www.youtube.com/)

#### 🧠 Search Engines

* Google, Bing, Yahoo, DuckDuckGo, Yandex, Baidu, Ask.com, Ecosia

#### 💻 Development Platforms

* [GitHub](https://github.com/)
* [GitLab](https://about.gitlab.com/)
* [Bitbucket](https://bitbucket.org/)
* [SearchCode](https://searchcode.com/)

#### 🧵 Forums & Communities

* [Reddit](https://www.reddit.com/)
* [StackOverflow](https://stackoverflow.com/)
* [Quora](https://quora.com)
* [CodeProject](https://www.codeproject.com/)

---

## 🖥️ Practical Setup

### Browsers Needed

* **Research Browser**: For live investigation + tracking steps.
* **Resource Browser**: For collecting and storing useful pages.

### Useful Add-ons

* [History Master](https://github.com/jiacai2050/history-master): Export browsing sessions.
* [SingleFile](https://addons.mozilla.org/en-US/firefox/addon/single-file/): Save webpages.

### Documentation Tools

```bash
sudo apt install npm jq -y
sudo npm install -g csvtojson
csvtojson < history.csv | jq .
```

---

## 📑 Detailed Structure

### Company Information

* Objectives, structure, employee count, departments.
* Services, products, clients.
* Location, physical security.
* Contact details, business reports.
* Sources:

  * Official Website
  * LinkedIn, Monster, Indeed, Glassdoor
  * Google/Earth Maps
  * PDF/Docx + Exif Analysis

### Infrastructure

* ASN, domains, DNS records, service provider.
* Exposed services, cloud storage, email setup.
* Tools:

  * `crt.sh`, `dnsdumpster`, `IP2Provider`, `Shodan`

### Leaks

* Archived versions from Archive.org.
* Search for breaches using HaveIBeenPwned.
* Files containing passwords or emails.
* Pastebin, GitHub, developer forums.
* Exif analysis of leaked documents.

---

## 🧾 Documentation

* Document **both results and methods used**.
* Browsing log (timestamp + query + URL).
* Save HTML snapshots.
* Store and analyze metadata (EXIF).

---

