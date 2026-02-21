## Implementation Steps

### Step 1: Install Sysmon on Windows


### 📥 Installation Steps

1. Download **Sysmon** from Microsoft
2. Use a **proper Sysmon configuration** (very important)

### ▶️ Install Command

```powershell
Sysmon64.exe -i sysmonconfig.xml
```

### 📌 Recommended Sysmon Configs

* **SwiftOnSecurity Sysmon config**
* **Olaf Hartong modular Sysmon config**

> ❗ Bad config = noisy logs
> ✅ Good config = SOC-level visibility

---

## 🔧 STEP 2: Install Wazuh Agent on Windows

### 🖥️ Agent Setup

1. Install the Wazuh Agent
2. Register the agent with the Wazuh Server
3. Confirm agent is connected

### ✅ Validation

* Agent appears in Wazuh Dashboard
* Agent status shows **Active**

---

## 🔧 STEP 3: Configure Wazuh to Collect Sysmon Logs

### 📄 Wazuh Agent Configuration (Windows)

Edit the Wazuh Agent configuration file and add:

```xml
<localfile>
  <location>Microsoft-Windows-Sysmon/Operational</location>
  <log_format>eventchannel</log_format>
</localfile>
```

### 🔄 Restart Wazuh Agent

```powershell
Restart-Service wazuh
```

---

## 🔧 STEP 4: Enable Sysmon Rules in Wazuh

Wazuh already includes:

* ✅ Sysmon decoders
* ✅ Sysmon detection rules

### 🧠 You Can Add Custom Rules For:

* Suspicious PowerShell execution
* Credential dumping techniques
* Living-Off-The-Land Binaries (LOLBins)

---

## 🔍 STEP 5: Generate Test Attacks (Validation)

Run the following commands on the Windows endpoint:

```powershell
whoami
net user
powershell -enc <base64>
```

### ✅ Expected Results

* Sysmon logs the activity
* Wazuh Agent forwards logs
* Alerts appear in Wazuh Dashboard

---

## 📊 STEP 6: Analyze in Wazuh Dashboard

Monitor and investigate:

* Process trees
* Parent / child process relationships
* Network connections
* MITRE ATT&CK technique mapping

---

---

### Detection and Alerting

Wazuh detection rules can identify:

* Suspicious PowerShell execution
* Credential dumping attempts
* Malware execution patterns
* Abnormal outbound network connections

All alerts are visible in the **Wazuh Dashboard**.

---

## 🔎 Example Detection Scenarios

* PowerShell execution with encoded commands
* Office applications spawning child processes
* Outbound connections from uncommon binaries
* Registry-based persistence techniques

---

## 🎯 SOC Use Cases

This project supports:

* Endpoint threat detection
* Incident investigation
* Malware analysis
* Threat hunting
* Compliance monitoring

---

## 🧠 Key Takeaway

> **Sysmon provides visibility.
> Wazuh provides intelligence.**

Together, they deliver powerful **endpoint monitoring and detection** comparable to commercial EDR solutions.


## 👤 Author

**Olusegun Fajobi**
Cybersecurity Engineer (Blue & Red Teamer)
GitHub: [https://github.com/samfajobi](https://github.com/samfajobi)

```
