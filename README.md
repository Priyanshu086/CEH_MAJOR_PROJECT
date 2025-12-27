# 🚨 Attack, Detect & Secure a Cloud Infrastructure (Azure)

![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Wazuh](https://img.shields.io/badge/Wazuh-00a9e0?style=for-the-badge&logo=wazuh&logoColor=white)
![Cybersecurity](https://img.shields.io/badge/Security-Red%20vs%20Blue-red?style=for-the-badge)

## 📌 Project Overview
This project simulates a **real-world enterprise cloud environment** to demonstrate the lifecycle of a cyber-attack. It covers how attacks are executed (Red Team), how they are detected using SIEM (Blue Team), and how the infrastructure is hardened to prevent future breaches.

---

## 🏗️ Infrastructure Architecture
The environment is hosted on **Microsoft Azure** using a segmented network approach.

* **Cloud Platform:** Microsoft Azure
* **Virtual Network:** Single VNet with multi-subnet segmentation

### Virtual Machines
| VM Name | Role | Purpose |
| :--- | :--- | :--- |
| **VM-1** | Internal Server | FreeIPA (LDAP/Kerberos), File Server |
| **VM-2** | Web Server (DMZ) | Apache Web Server |
| **VM-3** | SIEM Server | Wazuh (Log Monitoring & Analysis) |

---

## 🔴 Phase 1: Red Team (Attack Simulation)
In this phase, I acted as the adversary to identify and exploit vulnerabilities within the infrastructure.

### Attacks Performed
* **Reconnaissance:** Network scanning to map open ports and services using **Nmap**.
* **Brute-Force:** SSH credential harvesting using **Hydra**.
* **Web Enumeration:** Discovering hidden directories and sensitive config files using **Dirb**.
* **Data Probing:** Accessing unauthorized system files using Linux built-in tools.

### Tools Used
`Nmap` | `Hydra` | `Dirb` | `Linux CLI`

> [!IMPORTANT]
> All attacks were logged in real-time by the SIEM server to create a baseline for detection.

---

## 🔵 Phase 2: Blue Team (Detection & Hardening)
The defensive phase focused on analyzing the "digital breadcrumbs" left by the Red Team and closing the security gaps.

### 🔍 Log Analysis
I monitored the following log sources within **Wazuh**:
* **SSH logs (`auth.log`):** Detected failed login spikes and brute-force patterns.
* **Web logs (`apache2/access.log`):** Detected 404 spikes from directory enumeration.
* **System logs (`syslog`):** Monitored for unauthorized privilege escalation attempts.

### 🛠️ Security Hardening Measures
* **Identity:** Implemented SSH key-based authentication and disabled root login.
* **Network Security:** Configured Azure **Network Security Groups (NSG)** and **UFW** to restrict traffic.
* **Segmentation:** Isolated the Internal Server from direct DMZ access.
* **Service Hardening:** Patched Apache and removed default configurations.

---

## 🔁 Re-Attack & Validation
After hardening the systems, I repeated the Phase 1 attacks to verify the defenses:
* **Reduced Attack Surface:** Blocked ports resulted in failed reconnaissance.
* **Enhanced Alerting:** SIEM triggered high-severity alerts immediately upon suspicious activity.
* **Improved Results:** Clear difference in logs observed (Before vs. After).

---

## 📊 Results
* **Stronger Security Posture:** Transitioned from "Default-Allow" to "Least-Privilege" architecture.
* **Effective Detection:** 100% visibility of critical attack vectors via Wazuh.
* **Enterprise Architecture:** Successfully implemented a DMZ-Internal subnet separation.

---

## 📸 Screenshots
*Include your project screenshots here to demonstrate your work:*
* **Azure Deployment** (with student name visible)
* **Wazuh SIEM Dashboard**
* **Attack Logs (Before vs. After Hardening)**

---

## 🎓 Learning Outcomes
* Hands-on experience with **Red Team** exploit methodologies.
* Mastery of **Blue Team** log analysis and SOC operations.
* Cloud security configuration within **Microsoft Azure**.
* Incident Response and proactive system hardening.

---

## 👤 Author
**Priyanshu Dewangan**
*Cybersecurity Project – Azure Cloud*
