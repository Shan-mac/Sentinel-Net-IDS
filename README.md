# Sentinel-Net: Snort 3 Intrusion Detection System

## 🛡️ Project Overview
Sentinel-Net is a custom-configured Network Intrusion Detection System (NIDS) built using **Snort 3** on Kali Linux. It monitors network traffic in real-time to identify and alert on reconnaissance patterns like ICMP discovery and TCP Port Scanning.

## 🛠️ Technical Stack
- **OS:** Kali Linux
- **Engine:** Snort++ 3.12.1.0
- **Language:** Lua (Configuration)
- **Network Mode:** Bridged Adapter

## 🚀 Key Features
- **Real-time Monitoring:** Packet inspection on the `eth0` interface.
- **Custom Signatures:** Hand-written rules specifically tuned to detect `SYN` flags and ICMP probes.
- **Cross-Platform Testing:** Successfully detected attacks launched from a Windows 11 host.

---

## ⚙️ Configuration Process

### 1. Snort.lua Configuration
The first step was configuring the Snort 3 "brain" using Lua. I defined the network variables to protect the local subnet and pointed the engine to the custom rules file.

![screenshots/snort.png]
*Figure 1: Defining HOME_NET and including local.rules in snort.lua*

### 2. Local.rules Creation
Next, I authored custom detection signatures. These rules instruct Snort to generate alerts whenever ICMP packets or TCP SYN packets (indicating a port scan) are detected on the network.

![screenshots/rules.png]
*Figure 2: Custom signatures for ICMP and TCP Port Scan detection.*

---

## 📈 Detection Results

### 3. Final Execution & Alert Trigger
After validating the configuration, the Snort engine was launched in real-time alert mode. A scan was initiated from a remote Windows 11 machine using Nmap.

![screenshots/result.png]
*Figure 3: Snort 3 successfully identifying and logging the TCP Port Scan in real-time.*

---

## 📝 Conclusion
The project successfully demonstrates how a signature-based IDS can be deployed in a virtualized environment to gain visibility into network reconnaissance activities.
