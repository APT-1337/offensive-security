# WordPress Enumeration

## 🧠 What is WordPress?

[WordPress](https://wordpress.org/) is the most popular open-source Content Management System (CMS) that powers millions of websites globally. It allows users to easily create and manage websites through a user-friendly interface and a large library of plugins and themes. However, due to its popularity and extensibility, it is a common target for attackers.

---

## 🔍 Enumeration Overview

Enumeration is the process of gathering information about a target WordPress site to discover possible vulnerabilities. The goal is to collect details like version number, usernames, plugins, themes, and exposed files.

---

### 🔸 1. Identify WordPress Version

Check the page source for the following meta tag:
```html
<meta name="generator" content="WordPress 5.x.x" />
```

**Using cURL and grep:**
```bash
curl -s -X GET http://target.com | grep '<meta name="generator"'
```

---

### 🔸 2. Enumerate Plugins and Themes

Inspect the page source or use `curl` and `grep` to extract plugin and theme paths.

**Plugins:**
```bash
curl -s http://target.com | sed 's/href=/\n/g' | sed 's/src=/\n/g' | grep 'wp-content/plugins/' | cut -d"'" -f2
```

**Themes:**
```bash
curl -s http://target.com | sed 's/href=/\n/g' | sed 's/src=/\n/g' | grep 'themes' | cut -d"'" -f2
```

---

### 🔸 3. Enumerate Users

#### Method 1: Author ID
Visit:
```
http://target.com/?author=1
```
If it redirects to `/author/USERNAME/`, the user exists.

#### Method 2: JSON API
```bash
curl http://target.com/wp-json/wp/v2/users | jq
```

---

### 🔸 4. Check for xmlrpc.php

Check if the XML-RPC interface is enabled, which can be used for brute-force or method enumeration.

```bash
curl -X POST -d "<methodCall><methodName>system.listMethods</methodName><params><param><value>admin</value></param><param><value>PASSWORD</value></param></params></methodCall>" http://target.com/xmlrpc.php
```

---

### 🔸 5. Directory Indexing

Check if directory listing is enabled on plugin folders:
```bash
curl -s http://target.com/wp-content/plugins/plugin-name/ | html2text
```

---

### 🔸 6. Automated Enumeration with WPScan

[WPScan](https://github.com/wpscanteam/wpscan) is a powerful tool to scan WordPress sites.

**Example:**
```bash
wpscan --url http://target.com --enumerate u,ap --api-token YOUR_TOKEN
```

**Common Enumeration Flags:**
- `u` – Users
- `ap` – All Plugins
- `vp` – Vulnerable Plugins

---

Happy Enumerating! 🎯
