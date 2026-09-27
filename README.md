# CodeAlpha_Task-4
Network Intrusion Detection System using Suricata 
# CodeAlpha Task 4: Network Intrusion Detection System (IDS)

## Project Overview

This project implements a **Network Intrusion Detection System (IDS)** using **Suricata**, a powerful open-source network security monitoring tool. The system monitors network traffic in real-time, detects suspicious activities, and generates alerts based on 52,856+ detection rules.

---

## What is Suricata?

Suricata is a free, open-source network threat detection engine that:
- ✅ Monitors network traffic 24/7
- ✅ Detects known attacks and malware signatures
- ✅ Generates real-time alerts
- ✅ Supports IDS (monitoring) and IPS (blocking) modes
- ✅ Works on Linux, Windows, and macOS

---

## Task Requirements

### ✅ Requirement 1: Set up Network-Based IDS
- **Tool Used:** Suricata 8.0.6
- **Installation:** `sudo apt install suricata`
- **Status:** Successfully installed and running
- **Interface Monitored:** eth0

### ✅ Requirement 2: Configure Rules & Alerts
- **Rules Downloaded:** 52,856 detection rules
- **Source:** Emerging Threats Open (ETOpen)
- **Alert Formats:**
  - `fast.log` - Simple text alerts
  - `eve.json` - Detailed JSON alerts
  - `stats.log` - Performance statistics

### ✅ Requirement 3: Monitor Network Traffic Continuously
- **Status:** Active monitoring on eth0
- **Threads:** 2 worker threads + Flow Manager + Flow Receiver
- **Test Traffic Generated:**
  - Ping to 8.8.8.8
  - Network scan with nmap
  - HTTP requests with curl

### ✅ Requirement 4: Implement Response Mechanisms
- **Logging:** Enabled for all alert types
- **Alerts Detected:** 2,040+ events logged
- **Response Output:**
  - Text alerts to `fast.log`
  - JSON details to `eve.json`
  - Console real-time output
  - Activity logging to `suricata.log`

### ✅ Requirement 5: Visualize Detected Attacks (Optional)
- Alert summaries by classification
- Alert timeline visualization
- Severity level distribution
- Statistics tracking

---

## Installation & Setup

### Prerequisites
- Kali Linux (or any Linux distribution)
- Internet connection
- Admin/sudo access

### Step 1: Install Suricata
```bash
sudo apt update
sudo apt install suricata -y
suricata -V
Expected output: Suricata 8.0.6 RELEASE

Step 2: Verify Installation
suricata -V

Step 3: Download Detection Rules
sudo suricata-update
This downloads 52,856+ detection rules from Emerging Threats 

Step 4: Verify Rules
sudo wc -l /var/lib/suricata/rules/suricata.rules
Expected: ~68,000+ lines (52,856 rules)

RUNNING the IDS
Terminal 1 - Start Monitoring
sudo suricata -c /etc/suricata/suricata.yaml -i eth0

Terminal 2 - Generate Traffic
# Ping test
ping 8.8.8.8 -c 10

# Network scan
sudo nmap -sV localhost

# Web request
curl http://www.google.com

Checking Alerts & Results
View Simple Alerts
sudo tail -20 /var/log/suricata/fast.log

View Detailed JSON Alerts
sudo tail -10 /var/log/suricata/eve.json

Count Total Alerts
sudo wc -l /var/log/suricata/eve.json

Filter Only Alert Events
sudo grep '"event_type":"alert"' /var/log/suricata/eve.json | wc -l



