# Wazuh Installation & Setup Guide (SOC Lab)

## Overview
Wazuh is an open-source security platform used for **host-based intrusion detection (HIDS)**, **log analysis**, **file integrity monitoring**, **vulnerability detection**, and **SIEM/XDR capabilities**.  
This guide documents the step-by-step installation of a **Wazuh all-in-one deployment** for SOC lab and learning purposes.

---

## Architecture Used
- **Wazuh Manager**
- **Wazuh Indexer (OpenSearch-based)**
- **Wazuh Dashboard**
- All components installed on a **single Ubuntu server**

> This setup mirrors small-to-medium SOC environments and is ideal for labs.

---

## System Requirements

### Operating System
- Ubuntu Server 20.04 / 22.04 (Recommended)

### Minimum Hardware
- CPU: 2 cores (4 cores recommended)
- RAM: 4 GB (8 GB recommended)
- Disk: 50 GB free space
- Network: Internet access

---

## Step 1: Update the System
```bash
sudo apt update && sudo apt upgrade -y
sudo reboot
````

---

## Step 2: Set Hostname (Optional but Recommended)

```bash
sudo hostnamectl set-hostname wazuh-manager
```

Edit hosts file:

```bash
sudo nano /etc/hosts
```

Add:

```text
127.0.0.1 wazuh-manager
```

---

## Step 3: Download the Wazuh Installation Script

Wazuh provides an official installation script for quick and secure deployment.

```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
```

Make it executable:

```bash
chmod +x wazuh-install.sh
```

---

## Step 4: Run the All-in-One Installation

```bash
sudo ./wazuh-install.sh -a
```

This installs:

* Wazuh Manager
* Wazuh Indexer
* Wazuh Dashboard

⏳ Installation may take **10–20 minutes**.

---

## Step 5: Save Generated Credentials

At the end of installation, Wazuh will display credentials similar to:

```text
Username: admin
Password: <generated-password>
```

⚠️ **Save this securely** — it is required to access the dashboard.

---

## Step 6: Verify Wazuh Services

Check that all services are running:

```bash
sudo systemctl status wazuh-manager
sudo systemctl status wazuh-indexer
sudo systemctl status wazuh-dashboard
```

All services should show **active (running)**.

---

![Wazuh-setup-1](screenshots/wazuh-setup-1.png)

![Wazuh-setup-1](screenshots/wazuh-setup-2.png)

![Wazuh-setup-1](screenshots/wazuh-setup-3.png)

## Step 7: Access the Wazuh Dashboard

From your browser:

```text
https://<WAZUH_SERVER_IP>
```

Example:

```text
https://192.168.100.20
```

Accept the self-signed certificate warning.

Login using:

* **Username:** admin
* **Password:** (generated earlier)

---

![Wazuh-setup-1](screenshots/wazuh-setup-4.png)

![Wazuh-setup-1](screenshots/wazuh-setup-5.png)


## Step 8: Open Required Firewall Ports (If Enabled)

```bash
sudo ufw allow 1514/udp
sudo ufw allow 1515/tcp
sudo ufw allow 443/tcp
sudo ufw reload
```

---


## Features to Explore After Installation

* File Integrity Monitoring (FIM)
* Log collection and analysis
* MITRE ATT&CK mapping
* Vulnerability detection
* Active response
* Sysmon + Wazuh integration
* Suricata alerts ingestion

---

## Common Troubleshooting

### Dashboard Not Loading

```bash
sudo systemctl restart wazuh-dashboard
```

### Agent Not Connecting

* Check IP address
* Ensure ports are open
* Verify time synchronization

---

## Use Case in SOC Environment

This setup simulates a **real-world SOC deployment** where:

* Endpoints send logs to a central SIEM
* Alerts are correlated and visualized
* Analysts investigate security events using dashboards and rules

---



---

## Author

**Olusegun Fajobi**
Cybersecurity Engineer.
GitHub: [https://github.com/samfajobi](https://github.com/samfajobi)

---



