# 🛡️ Zeek + Splunk Home Network Monitor

This project documents my successful implementation of a home network monitoring solution using **Zeek** for deep packet inspection and **Splunk** for log analysis and visualization. Since my AT&T router does not support syslog forwarding, I built a workaround using open-source tooling to simulate a mini SOC (Security Operations Center) environment.

---

## 📡 Project Overview

🔹 **Goal**: Gain full visibility into traffic on my home network  
🔹 **Tools Used**:  
- **Zeek**: Open-source network security monitor that passively logs network activity  
- **Splunk**: SIEM platform used to ingest and visualize logs  
- **Linux (Ubuntu)**: Base OS used to capture and analyze traffic

---

## 🧠 Key Learnings & Challenges

- GitHub's removal of password authentication required use of a **Personal Access Token**
- Zeek was **not available via apt** due to a broken repository
- Successfully compiled Zeek **from source** after resolving:
  - Missing build tools: `make`, `cmake`, `swig`
  - Library dependencies: `libpcap-dev`, `zlib1g-dev`, `python3-dev`, etc.
- Configured Zeek to monitor my active network interface and output real-time logs
- Integrated Zeek logs into Splunk using file-based ingestion

---

## 🔍 Zeek Logs Ingested into Splunk

- `conn.log`: Connection summaries
- `dns.log`: DNS queries and responses
- `ssl.log`: SSL/TLS certificate details
- `weird.log`: Unusual network behavior
- Optional: `http.log`, `files.log`, and others depending on traffic

---

## 🖥️ Splunk Configuration

- Added Zeek log directory (`/usr/local/zeek/logs/current/`) as a file input
- Created a custom **sourcetype** called `zeek`
- Indexed logs into a separate index for better query organization
- Built visual dashboards for:
  - Top talkers (internal devices by connection count)
  - Frequent DNS lookups
  - Detected anomalies and protocol distribution

---

## 📂 Repo Structure

```bash
zeek-splunk-home-network-monitor/
├── README.md
├── zeek-setup.md               # Instructions to build and run Zeek
├── splunk-setup.md             # Steps to ingest logs into Splunk
├── zeek-sample-logs/           # Optional sample logs (anonymized)
└── dashboard-screenshots/      # Screenshots of Splunk visualizations
