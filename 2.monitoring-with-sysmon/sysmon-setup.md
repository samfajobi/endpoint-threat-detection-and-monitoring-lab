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

2. Download **Sysmon.zip**

3. Extract contents to:

```
C:\Tools\Sysmon
```

You should see:

```
Sysmon.exe
Sysmon64.exe
```

---

# Step 2 – Download a Sysmon Configuration File

Sysmon requires a configuration file to define what events to log.

Recommended community config:
SwiftOnSecurity Sysmon config

Download from:
https://github.com/SwiftOnSecurity/sysmon-config

Save as:

```
C:\Tools\Sysmon\sysmonconfig.xml
```

---

# Step 3 – Install Sysmon

Open **PowerShell as Administrator**

Navigate to Sysmon directory:

```powershell
cd C:\Tools\Sysmon
```

Install Sysmon with config:

```powershell
.\Sysmon64.exe -accepteula -i sysmonconfig.xml
```

If successful, you will see:

```
Sysmon installed.
```

---

# Step 4 – Verify Sysmon Installation

Check if service is running:

```powershell
Get-Service Sysmon64
```

Or:

```powershell
sc query Sysmon64
```

It should show:

```
Running
```

---


```



