# Cybersecurity / Google Hacking

## 0-Introduction

# 📚 Google Hacking Introduction

## 🧐 What is Google Dorking?

Google Dorking (also called Google Hacking) is the art of using advanced search queries on Google to find sensitive or hidden information that is publicly accessible but not properly secured. It uses special operators known as "**dorks**" to perform highly specific searches.

---

## ⚡️ Why is it Important?

- **Security Testing**: Find exposed files, vulnerable services, and misconfigurations.
    
- **Bug Bounty Hunting**: Discover public leaks related to targets.
    
- **Reconnaissance**: Gather valuable information during penetration testing.
    
- **Learning**: Understand how data can accidentally become exposed.
    
---

## 1-Basic Dorks

# 🔧 Basic Google Hacking Dorks

Sub Domain enumeration
> -`site:*.example.com -site:www.example.com`

Common Google Dorks used to find exposed files or pages:

- `intitle:"Index of /" "config.php" wordpress demo`
    
    > Search for exposed WordPress configuration files.
    
- `intitle:"Index of /" "passwords.txt"`
    
    > Locate exposed text files containing passwords.
    
- `intitle:"Index of /" "admin" "password.txt"`
    
    > Search for admin credentials files.
    
- `allinurl:passwords.txt email`
    
    > Look for password lists that include email addresses.
    
- `intitle:"Index of" ".htpasswd"`
    
    > Find exposed `.htpasswd` authentication files.
    
- `allinurl:/cgi-bin/ ? password`
    
    > Access CGI scripts that might leak passwords.
    

---

## 2-Sensitive Information Dorks

# 🔐 Sensitive Information Search Dorks

Queries used to find sensitive documents and credentials:

- `site:targetwebsite.com ext:xls password`
    
- `site:targetwebsite.com ext:xlsx password`
    
- `site:targetwebsite.com ext:doc password`
    
- `site:targetwebsite.com ext:docx password`
    
- `site:targetwebsite.com filetype:pdf username password`
    
- `site:targetwebsite.com filetype:ppt username password`
    

> These dorks target specific file formats (Excel, Word, PDF, PowerPoint) that may contain usernames and passwords.

---

## 3-Vulnerable Sites Dorks

# 🛡️ Vulnerable Website Dorks

Identifying websites running vulnerable or outdated platforms:

- `intext:Drupal "Powered By Drupal forums"`
    
- `"powered by PHPmotion v3"`
    
- `"Powered by osCommerce"`
    
- `"Powered by TinyMCE"`
    
- `"Powered by Vanilla forums"`
    
- `"Powered by vBulletin"`
    
- `"Powered by WordPress"`
    

> Detect which CMS/platform a website is using to exploit known vulnerabilities.

---

## 4-Other Useful Dorks

# 📂 Other Useful Google Hacking Dorks

Various searches that uncover administrative panels, server info, and backups:

- `cache:www.targetwebsite.com`
    
- `inurl:/proc/self/cwd`
    
- `intitle:"WAMPSERVER homepage"`
    
- `inurl:/muieblackcat`
    
- `inurl:admin.php site:targetwebsite.com`
    
- `intext:phpMyAdmin SQL Dump filetype:sql`
    
- `inurl:/main.php?x=`
    
- `inurl:/elfinder/connector.php`
    

### Map-related Dorks

- `Map:example.com`
    
- `Map:example.com site:mapquest.com`
    
- `Map:example.com inurl:map`
    
- `Map:example.com intitle:map`
    

### Link-related Dorks

- `Link:example.com`
    
- `Link:example.com "link directory"`
    
- `Link:example.com inurl:directory`
    
- `Link:example.com site:blogspot.com`
    

### Phonebook-related Dorks

- `Phonebook:example.com`
    
- `Phonebook:john smith site:example.com`
    
- `Phonebook:+"firstname lastname" OR "lastname firstname"`
    
- `Phonebook:+"phone number" OR "cell number"`
    

### Info-related Dorks

- `Info:example.com`
    
- `Info:example.com allinurl:admin`
    
- `Info:example.com allinurl:config`
    
- `Info:example.com filetype:conf conf`
    

### Cache-related Dorks

- `Cache:example.com`
    
- `Cache:example.com filetype:doc pdf xls`
    
- `Cache:"example.com" "MySQL dump"`
    
- `Cache:example.com intext:some_one_secret_file`
    

### Miscellaneous Useful Dorks

- `intitle:"index of" "apache at"`
    
- `intitle:"Index of /admin"`
    
- `intitle:"webcamXP 5" inurl:8080`
    
- `intitle:"Welcome to nginx!" intext:"Welcome to our server!"`
    
- `inurl:cv OR filetype:pdf "cv"`
    
- `inurl:/view/view.shtml`
    
- `inurl:/admin`
    
- `inurl:/phpinfo.php`
    
- `inurl:/wp-content/uploads/`
    
- `intext:"sql syntax near" OR intext:"syntax error has occurred"`
    
- `intext:"Powered by phpBB" inurl:/viewtopic.php`
    
- `intext:"MyBB SQL Error" site:example.com`
    
- `intext:"WordPress" inurl:"wp-config.php" filetype:log`
    
- `filetype:xls site:example.com`
    
- `filetype:doc site:example.com`
    
- `filetype:pem private key site:example.com`
    
- `filetype:config site:example.com`
    

---

## 5-Advanced Dorks

# 🔥 Advanced Google Hacking Dorks

Complex and targeted search queries for deeper information discovery:

- `intitle:phpmyadmin inurl:server_privileges OR intitle:"login for server * at"`
    
- `site:targetwebsite.com inurl:/phpmyadmin/* ext:sql ext:sql.gz ext:sql.bz2`
    
- `site:urlscan.io "activity"`
    
- `intitle:"Index of" .ssh/id_rsa`
    
- `intext:"Fill out the form below completely to change your password" site:.edu`
    
- `filetype:log intext:password`
    
- `inurl:twiki/bin/view/TWiki/WebHome`
    
- `intitle:"Please login with admin pass"`
    
- `inurl:/vpn/tmindex.html`
    

> These advanced searches can expose database dumps, password reset forms, SSH keys, and VPN login portals.
