
# 🌐 HTTP & HTTPS – Full Note for eWPT Preparation

---

## 📘 What is HTTP and HTTPS?

- **HTTP (HyperText Transfer Protocol)**: A protocol used to transfer data between the client (browser) and the server.
- **HTTPS**: HTTP + **TLS encryption** to protect sensitive data (passwords, cookies, etc.) during transmission.

---

## ⚙️ How HTTP/HTTPS Works

1. **Client (Browser)** sends an HTTP request.
2. **Server** processes the request and sends a response.
3. Communication happens over HTTP or HTTPS.

---

## 🔧 HTTP Methods (Verbs)

- `GET`: Retrieve data (used when browsing pages).
- `POST`: Send data (e.g., login forms).
- `PUT`: Update data.
- `DELETE`: Remove data.
- `HEAD`: Same as GET but without the body.
- `OPTIONS`: Ask server what methods are allowed.

> ⚠️ Certain attacks depend on the method used (e.g., XSS with GET, CSRF with POST).

---

## 📤 HTTP Request Structure

Example:

GET /login HTTP/1.1 
Host: example.com 
User-Agent: Mozilla/5.0 
Cookie: session=abc123

### Request Parts:

- **Request Line**: Method + Path + Version.
- **Headers**: Extra info like cookies, user-agent, etc.
- **Body**: Present only in POST/PUT (contains form data).

---

## 📥 HTTP Response Structure

Example:

HTTP/1.1 200 OK 
Content-Type: text/html 
Set-Cookie: session=xyz456

<html>...</html> ```

### Response Parts:

- **Status Line**: Includes response code.
    
- **Headers**: Metadata like cookies, content type.
    
- **Body**: The actual web content.

## 📊 Common HTTP Status Codes

### 2xx Success:

- `200 OK`: Success – Normal behavior.
    

### 3xx Redirection:

- `301 Moved Permanently`: Redirect.
    
- `302 Found`: Redirect – May lead to Open Redirect issues.
    

### 4xx Client Error:

- `400 Bad Request`: Malformed request – May indicate WAF.
    
- `401 Unauthorized`: Authentication required – Try bypass techniques.
    
- `403 Forbidden`: Access denied – Try path bypassing.
    
- `404 Not Found`: Resource missing – Might be exploitable.
    

### 5xx Server Error:

- `500 Internal Server Error`: Server crashed – Possible vulnerabilities (e.g., LFI, SQLi).
    

---

## 🔐 HTTPS - How Encryption Works

1. Browser requests secure connection.
    
2. Server sends TLS certificate.
    
3. Browser verifies certificate.
    
4. Both exchange encryption keys.
    
5. All further communication is encrypted.
    

