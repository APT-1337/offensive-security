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



## ✅ Quick Reference


| **Command** | **Description** |
| --------------|-------------------|
| `curl -h` | cURL help menu |
| `curl inlanefreight.com` | Basic GET request |
| `curl -s -O inlanefreight.com/index.html` | Download file |
| `curl -k https://inlanefreight.com` | Skip HTTPS (SSL) certificate validation |
| `curl inlanefreight.com -v` | Print full HTTP request/response details |
| `curl -I https://www.inlanefreight.com` | Send HEAD request (only prints response headers) |
| `curl -i https://www.inlanefreight.com` | Print response headers and response body |
| `curl https://www.inlanefreight.com -A 'Mozilla/5.0'` | Set User-Agent header |
| `curl -u admin:admin http://<SERVER_IP>:<PORT>/` | Set HTTP basic authorization credentials |
| `curl  http://admin:admin@<SERVER_IP>:<PORT>/` | Pass HTTP basic authorization credentials in the URL |
| `curl -H 'Authorization: Basic YWRtaW46YWRtaW4=' http://<SERVER_IP>:<PORT>/` | Set request header |
| `curl 'http://<SERVER_IP>:<PORT>/search.php?search=le'` | Pass GET parameters |
| `curl -X POST -d 'username=admin&password=admin' http://<SERVER_IP>:<PORT>/` | Send POST request with POST data |
| `curl -b 'PHPSESSID=c1nsa6op7vtk7kdis7bcnbadf1' http://<SERVER_IP>:<PORT>/` | Set request cookies |
| `curl -X POST -d '{"search":"london"}' -H 'Content-Type: application/json' http://<SERVER_IP>:<PORT>/search.php` | Send POST request with JSON data |

#### APIs
| **Command** | **Description** |
| --------------|-------------------|
| `curl http://<SERVER_IP>:<PORT>/api.php/city/london` | Read entry |
| `curl -s http://<SERVER_IP>:<PORT>/api.php/city/ \| jq` | Read all entries |
| `curl -X POST http://<SERVER_IP>:<PORT>/api.php/city/ -d '{"city_name":"HTB_City", "country_name":"HTB"}' -H 'Content-Type: application/json'` | Create (add) entry |
| `curl -X PUT http://<SERVER_IP>:<PORT>/api.php/city/london -d '{"city_name":"New_HTB_City", "country_name":"HTB"}' -H 'Content-Type: application/json'` | Update (modify) entry |
| `curl -X DELETE http://<SERVER_IP>:<PORT>/api.php/city/New_HTB_City` | Delete entry |


---
