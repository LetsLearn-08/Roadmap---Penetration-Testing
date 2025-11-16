# 🧪 Lab: Web Browsing (HTTP)

## 🎯 Objective
Capture and analyze **HTTP GET and POST requests** using Wireshark to understand how web browsing works at the packet level.

---

## 🛠 Setup

- Environment: VirtualBox lab  
- Target: Metasploitable2 or any reachable web server (e.g., `http://testphp.vulnweb.com`)  
- Tool: Wireshark (latest version)  
- Browser: Firefox/Chrome or `curl` for command‑line requests  

---

## 🚀 Steps

1. **Start Wireshark** and select your active network interface.  
2. **Open a browser** and visit a test site (e.g., `http://example.com`).  
   - Alternatively, run:  

      ```bash
      curl -v http://example.com
      ```  
3. **Apply a display filter** in Wireshark:
   
    ```
    http
    ```
5. Observe the captured packets:
- **HTTP GET requests** (browser requesting a page/resource).  
- **HTTP POST requests** (form submissions or data uploads).  

---

## 🔍 What to Look For

- **Request line:** `GET /index.html HTTP/1.1`  
- **Headers:** Host, User‑Agent, Accept, Content‑Type  
- **Response codes:** `200 OK`, `404 Not Found`, `302 Redirect`  
- **Payloads:** POST data in the packet details pane  
- **TCP handshake:** Notice the 3‑way handshake before HTTP traffic begins  

---

## 📸 Documentation

- Screenshot: HTTP GET request packet details.  
- Screenshot: HTTP POST request with payload visible.  
- Notes: Status codes, headers, and differences between GET vs POST.  

---

## ✅ Outcome

By completing this lab, you will:  
- Understand how browsers request and receive web content.  
- Learn to filter and analyze HTTP traffic in Wireshark.  
- Build a foundation for detecting suspicious web activity in future labs.
   
