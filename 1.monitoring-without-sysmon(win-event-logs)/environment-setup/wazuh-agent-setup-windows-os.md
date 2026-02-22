# Windows Server Enrollment into Wazuh

This document outlines the steps used to **enroll a Windows Server host into Wazuh** as part of a SOC monitoring and detection lab.
The goal is to enable **centralized log collection, endpoint visibility, and security monitoring** from Windows Server into the Wazuh manager.

---

## Prerequisites

Before enrolling the Windows Server, ensure the following:

* Wazuh Manager is installed and running
* Wazuh Dashboard is accessible
* Network connectivity exists between the Windows Server and Wazuh Manager
* Administrator privileges on the Windows Server

---

## Step 1: Create a Wazuh Agent Entry

1. Log in to the **Wazuh Dashboard**
2. Navigate to:
   **Agents → Deploy new agent**

![Wazuh-setup-1](screenshots/wazuh-setup-5.png) 

3. Select:
* **Operating System:** Windows
* **Architecture:** (x64 or x86 depending on your server)

![Wazuh-setup-1](../screenshots/wazuh-setup-6.png)

![Wazuh-setup-1](../screenshots/wazuh-setup-6a.png)

4. Copy the generated **agent installation and enrollment commands**

![Wazuh-setup-1](../screenshots/wazuh-setup-6c.png)

---

## Step 2: Install the Wazuh Agent on Windows Server

1. Log in to the Windows Server
2. Open **PowerShell as Administrator**

![Wazuh-setup-1](../screenshots/wazuh-setup-7.png)

3. Run the provided Wazuh agent installation command, for example:

```powershell
Invoke-WebRequest -Uri https://package..........
```
![Wazuh-setup-1](../screenshots/wazuh-setup-7a.png)

*(Version may vary depending on your Wazuh release)*

---

## Step 3: Enroll the Agent with the Wazuh Manager

After installation, enroll the agent by running the enrollment command copied from the dashboard:

```powershell
"C:\Program Files (x86)\ossec-agent\agent-auth.exe" -m <WAZUH_MANAGER_IP>
```

This command registers the Windows Server with the Wazuh Manager.

---

## Step 4: Start the Wazuh Agent Service

Start and verify the agent service:

```powershell
net start wazuh
```
![Wazuh-setup-1](../screenshots/wazuh-setup-7a.png)

Confirm the service is running:

```powershell
sc query wazuh
```

---

