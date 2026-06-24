# ⚡ SERVER WATCHDOG ⚡
**Advanced Network Telemetry & Automated Incident Recovery Core**

[![Version](https://img.shields.io/badge/Version-v20.0-00FF41.svg)]()
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-blue.svg)]()
[![License](https://img.shields.io/badge/License-MIT-green.svg)]()

**Server Watchdog** is a lightweight, cross-platform telemetry utility designed for system administrators and IT professionals. It provides continuous, real-time monitoring of internal network infrastructure, specific service ports, and external WAN health. 

Equipped with a highly responsive "Matrix-style" visual dashboard, smart notification throttling via Discord, and automated recovery execution, Server Watchdog ensures you maintain absolute oversight of your critical infrastructure.

---

## 🌟 Enterprise Features

* **Dual-Layer Telemetry:** Asynchronous polling tracks internal IPv4 nodes (every 60s) and external public DNS/Domains (every 15m) simultaneously.
* **TCP Service Polling:** Beyond standard ICMP Pings, directly monitor critical service ports (e.g., `192.168.1.10:8006` for hypervisors, `:80` for web servers).
* **Smart Incident Throttling:** Intelligent state-tracking prevents Discord spam. Alerts are fired exactly once upon connection failure, and once upon restoration.
* **Automated Recovery Execution:** Instantly trigger localized `.bat` or `.sh` scripts to restart crashed services or send Wake-on-LAN packets the exact moment a node goes down.
* **Cross-Platform Hardware Diagnostics:** Real-time localized CPU and RAM health polling built-in.
* **Zero-Dependency Deployment:** Compiled as a standalone executable. No Python installation or background dependencies required.

---

## 🚀 Deployment Guide

### 1. Download & Initialize
1. Navigate to the [Official Releases Page](https://github.com/OmarTechMe/Server-Watchdog/releases/).
2. Download the latest `ServerWatchdog.exe` binary.
3. Place the executable in a dedicated operational directory (the software will automatically generate its configuration and log files in this directory).
4. Run the executable. 

### 2. Configure Discord Integrations
To route telemetry alerts to your mobile device or workstation, connect the software to your Discord server:
1. In your Discord Server, create two channels: `#internal-alerts` and `#wan-alerts`.
2. Navigate to **Channel Settings** > **Integrations** > **Webhooks**.
3. Create a **New Webhook**, name it (e.g., "Telemetry Node"), and click **Copy Webhook URL**.
4. Paste these URLs into the corresponding fields at the top of the Server Watchdog interface.

### 3. Define Monitoring Targets
* **Local Targets:** Enter your internal IP addresses (one per line). Append a port to track specific services (e.g., `10.0.0.5:22`).
* **Public Targets:** Enter standard WAN health targets (e.g., `google.com`, `1.1.1.1`) to monitor your facility's overall ISP connection.

Click **▶ INITIATE UPLINK** to lock in your configuration and begin active scanning. Your settings are permanently saved to a localized JSON file.

---

## 🔧 Automated Incident Recovery (AIR)

Server Watchdog can actively repair your network instead of just reporting it. 

If the **Enable Auto-Recovery Scripts** module is active, the software will scan its root directory for a corresponding script whenever a node drops offline.

**Example Scenario:**
If the database server at `192.168.1.50` crashes, the Watchdog will search for and execute:
* `recover_192_168_1_50.bat` (Windows)
* `recover_192_168_1_50.sh` (Linux)

**Example Batch Script (`recover_192_168_1_50.bat`):**
```bat
@echo off
:: Attempt to restart the Apache service via SSH
ssh admin@192.168.1.50 "sudo systemctl restart apache2"
echo Recovery protocol executed.
