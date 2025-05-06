# 🛠️ cURL Tool – Complete Beginner's Guide

`cURL` is a powerful command-line tool used to send and receive HTTP/HTTPS requests (and other protocols) directly from the terminal. It's extremely useful for testing web applications and APIs.

---

## ✅ What is cURL Used For?

- Testing REST APIs
- Sending and receiving files
- Inspecting HTTP headers
- Submitting login forms
- Sending various HTTP request types (GET, POST, PUT, DELETE...)

---

## ⚙️ Basic Command Structure

```bash
curl [options] [URL]
```

---

## 📥 Simple GET Request (Default)

```bash
curl https://example.com
```

🔹 Sends a GET request and returns the page content.

---

## 🔍 Show Response Headers

```bash
curl -i https://example.com
```

🔹 `-i`: Includes the HTTP response headers in the output.

---

## 📤 POST Form Data

```bash
curl -X POST -d "username=admin&password=1234" https://example.com/login
```

🔹 `-X POST`: Sets the request method to POST  
🔹 `-d`: Sends form-encoded data

---

## 📤 Send JSON Data

```bash
curl -X POST -H "Content-Type: application/json" -d '{"user":"admin", "pass":"1234"}' https://example.com/api/login
```

🔹 `-H`: Adds a custom HTTP header  
🔹 `-d`: Contains the JSON payload as a string

---

## 📥 Download a File

```bash
curl -O https://example.com/file.zip
```

🔹 `-O`: Saves the file with its original name from the URL.

---

## 💾 Save Response to File

```bash
curl https://example.com -o saved_page.html
```

🔹 `-o`: Saves the output to a file you name.

---

## 🔁 Follow Redirects

```bash
curl -L http://example.com
```

🔹 `-L`: Follows HTTP 3xx redirects to the final destination.

---

## 🔐 Basic Authentication

```bash
curl -u username:password https://example.com/secure
```

🔹 `-u`: Sends a username and password using Basic Auth.

---

## 📜 Send Custom Headers

```bash
curl -H "X-Custom-Header: value" https://example.com
```

---

## 🚀 Send DELETE Request

```bash
curl -X DELETE https://example.com/item/5
```

---

## 🧪 Send OPTIONS Request

```bash
curl -i -X OPTIONS https://example.com
```

---

## 🧠 Tips

- Use `man curl` or `curl --help` to explore all available options.
- Extremely useful for testing RESTful APIs.
- Handy for debugging web security from the terminal.

---

## ✅ Quick Reference

| Command | Description |
|---------|-------------|
| `curl URL` | Send GET request |
| `-i` | Include headers in response |
| `-X POST` | Change request method |
| `-d` | Send request body data |
| `-H` | Add custom header |
| `-o` / `-O` | Save output to file |
| `-u` | Basic Authentication |
| `-L` | Follow redirects |

---
