# 🚨 Man-in-the-Middle (MITM) Attack Demo

## ✅ Overview

This project demonstrates a simple **Man-in-the-Middle (MITM) Attack** in a fully isolated, local environment.  
It simulates how an attacker can intercept username and password sent over **plain HTTP** using `mitmproxy` and a custom Python HTTP server.

---

## ⚡ Why This Demo Matters

⚡️ Real-world websites transmitting sensitive data over HTTP are vulnerable to interception.  
⚡️ This demo teaches the importance of using HTTPS (SSL/TLS encryption) to protect data in transit.

---

## ✅ Project Structure

| Filename       | Purpose |
|--------------|----------|
| `server.py`    | Runs a simple HTTP server with a login form (receives username & password). |
| `intercept.py` | mitmproxy script that automatically logs intercepted POST request data. |

---

## ✅ ⚙️ Setup & Usage Instructions

### ▶️ 1️⃣ Install Dependencies

```bash
sudo apt update
sudo apt install python3 python3-venv

▶️ 2️⃣ Create Virtual Environment
python3 -m venv mitm-env
source mitm-env/bin/activate
pip install mitmproxy bcrypt==4.0.1

▶️ 3️⃣ Turn OFF Internet

👉 Ensure your laptop is fully offline during the demo.

▶️ 4️⃣ Run HTTP Server (Terminal 1)
python3 server.py


👉 Server URL: http://<local-IP>:8080

▶️ 5️⃣ Run mitmproxy (Terminal 2)
mitmproxy --mode regular -p 8081 --listen-host 0.0.0.0 -s intercept.py

▶️ 6️⃣ Configure Browser Proxy

HTTP Proxy: 127.0.0.1

Port: 8081

▶️ 7️⃣ Perform the Demo

Open browser → Visit:

http://<local-IP>:8080


Enter dummy credentials:

Username: testuser

Password: mypassword

Submit the form →
👉 Intercepted credentials will appear in the mitmproxy terminal.

✅ ⚠️ Important Notes

✔️ Do NOT run on public networks.
✔️ Fully educational, safe environment.
✔️ Helps understand the importance of HTTPS.
