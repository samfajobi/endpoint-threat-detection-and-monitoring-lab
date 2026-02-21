# Windows Endpoint Monitoring Without Sysmon

This profile demonstrates endpoint monitoring using **native Windows Event Logs only**.

## 📌 Use Case
- Environments where Sysmon cannot be deployed
- Legacy systems
- High-restriction corporate endpoints

## 📥 Log Sources
- Security Event Log
- System Event Log
- Application Event Log

## 🔎 Example Detections
- Failed logon attempts
- Successful logon anomalies
- Service installation
- Account privilege changes

## ⚠️ Limitations
- Limited process visibility
- Reduced network telemetry
- Lower fidelity investigations

This profile represents **baseline SOC visibility**.
