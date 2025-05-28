# 📊 Splunk Setup Guide for Zeek Log Ingestion

This guide explains how to configure Splunk to ingest and analyze logs from **Zeek**, a powerful network security monitoring tool. With this setup, you can visualize real-time DNS queries, network flows, SSL usage, and more from your home network.

---

## ✅ Prerequisites

- Zeek is installed and actively logging (see [`zeek-setup.md`](./zeek-setup.md))
- Splunk Enterprise or Splunk Free is installed and running locally
- You have access to Splunk Web at:  
  `http://localhost:8000` or `http://<hostname>:8000`

---

## 🧭 Step 1: Launch Splunk

Start Splunk if it’s not already running:

```bash
sudo /opt/splunk/bin/splunk start
