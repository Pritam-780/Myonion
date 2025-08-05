# 🧅 MyOnion - Host a .onion Website with Python (in Termux)

This project allows you to host a `.onion` website from your Android phone using **Python's HTTP server** and **Tor** via Termux. No PHP or root needed.

---

## ⚙️ Features

- Hosts a Tor Hidden Service
- Simple Python web server (no PHP or Apache)
- Runs fully in Termux on Android
- Auto-generates `.onion` URL
- Lightweight and fast setup

---

## 📦 Requirements

Install required tools in Termux and clone the project:

```bash
pkg update && pkg upgrade
pkg install python tor git
```
# 1. Update packages
```
pkg update && pkg upgrade
````

# 2. Install required tools
```
pkg install python tor git
```

# 3. Clone your GitHub repo
```
git clone https://github.com/Pritam-780/Myonion.git
```
# 4. Go into your project folder
```
cd Myonion
```
# 5. Create Tor Configuration File
This command creates the `torrc` file that tells Tor where to create the `.onion` service and how to forward requests to your Python server.

```bash
echo -e "HiddenServiceDir /data/data/com.termux/files/home/.tor/hidden_service3\nHiddenServicePort 80 127.0.0.1:8080" > torrc
````
## 🔍 Step 6: Verify the torrc File

After creating the configuration file, make sure it looks correct:
```
cat torrc
```
You should see something like:⬇️

HiddenServiceDir /data/data/com.termux/files/home/.tor/hidden_service3
HiddenServicePort 80 127.0.0.1:8080
---
# 5. Copy torrc file to correct location
```
cp torrc ~/.torrc
```

# 6. Start Python web server (on port 8080)
```
nohup python3 -m http.server 8080 > server.log 2>&1 &
```
# 7. Start Tor in background
```
nohup tor -f ~/.torrc > tor.log 2>&1 &
```
# 8. Wait 10-15 seconds, then get your .onion link
```
cat ~/.tor/hidden_service3/hostname
```

# 9. To edit your HTML site
```
nano index.html
```
# 10. To stop the server anytime
```
pkill python3
pkill tor
```
# ---------------------------------------------------------------
# ⚠️ DISCLAIMER:
# This script is for educational and personal use only.
# The author does not take any responsibility for misuse or abuse.
# Do not use this to host or distribute illegal content.
# Use responsibly and at your own risk.
#
# 📢 Join our Telegram channel for updates: https://t.me/harmfulapk
# ---------------------------------------------------------------
