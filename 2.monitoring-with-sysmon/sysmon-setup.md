# Sysmon + Wazuh Integration Guide (Windows Endpoint Monitoring)

## Overview

This guide walks through installing **Sysmon (System Monitor)** on a Windows endpoint and integrating it with **Wazuh** for enhanced endpoint visibility and detection.

Sysmon provides deep telemetry such as:

- Process creation (with command line)
- Network connections
- File creation time changes
- Registry modifications
- Driver loads
- DNS queries

When integrated with Wazuh, this significantly improves detection capabilities.

---

# Architecture

```
Windows Endpoint
   ├── Sysmon (Event Logging)
   ├── Windows Event Log
   └── Wazuh Agent
           ↓
      Wazuh Manager
           ↓
      Wazuh Dashboard
```

---

# Prerequisites

- Windows 10 / 11 endpoint
- Administrator privileges
- Wazuh Agent installed and connected
- Internet access (to download Sysmon)
- PowerShell access

---

# Step 1 – Download Sysmon

1. Go to Microsoft Sysinternals official page:
   https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon

2. 




