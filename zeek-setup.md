# 🛠️ Zeek Setup Guide (Ubuntu/Linux)

This guide walks through installing and configuring **Zeek**, a powerful open-source network monitoring tool, on a Linux system for home network visibility.

---

## ⚙️ Why Zeek?

Zeek (formerly Bro) passively monitors network traffic and generates rich logs for:
- DNS lookups
- SSL/TLS certificates
- HTTP activity
- Network anomalies (`weird.log`)
- Connection metadata (`conn.log`)

This makes it a great tool for home labs, SOC simulations, and threat detection.

---

## 📥 Step 1: Install Required Build Tools

Zeek isn’t always available via apt, and public Zeek repositories may be down. So we’ll build it from source.

Run:
```bash
sudo apt update
sudo apt install -y cmake make build-essential \
libpcap-dev python3-dev zlib1g-dev libssl-dev \
bison flex libkrb5-dev swig libcurl4-openssl-dev
