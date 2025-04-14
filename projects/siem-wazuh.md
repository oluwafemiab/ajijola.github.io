# 📊 Security Information and Event Management (SIEM) System with Wazuh & ntopng

**Author:** Ajijola Oluwafemi Blessing    
**Tools Used:** Wazuh, ntopng, Suricata, Metasploit, Hydra, Kali Linux, Logstash, Elasticsearch, VirtualBox



## 🔍 Overview

This project involved the design and deployment of a **lightweight SIEM system** using **Wazuh** for log analysis and endpoint monitoring, and **ntopng** for real-time network flow visualization. The system was tested using simulated attacks to analyze its effectiveness in **intrusion detection**, **log correlation**, and **network threat awareness**.



## 🧱 Objectives

- Set up a Wazuh SIEM platform and enroll monitored endpoints  
- Integrate ntopng for traffic inspection and network security metrics  
- Simulate brute-force, scanning, and exploit attacks from a Kali attacker VM  
- Analyze captured logs for detection accuracy and classification  
- Visualize threat activity and attack patterns in real-time dashboards



## 🔧 Tools & Architecture

**SIEM Core**:  
- **Wazuh Manager** – Central log collector and analyzer  
- **Wazuh Agent** – Installed on monitored endpoint  
- **Kibana** – Visual dashboard for Wazuh alerts  
- **Elasticsearch** – Stores structured event logs

**Network Monitoring**:  
- **ntopng** – Visualizes flows, traffic types, and protocol usage  
- **Suricata (optional)** – Network-based intrusion detection engine

**Attack Simulation Tools**:  
- **Hydra** – Brute-force attack generator  
- **Metasploit** – Payload and exploit tester  
- **Nmap** – Service scanner and OS fingerprinting  
- **Swaks** – SMTP spoofing test



## 🌐 Network Topology

```
Kali Attacker VM
      ↓
  Monitored Endpoint VM (Ubuntu)
      ↓
  Wazuh Manager + ntopng Server (SIEM)
```

All systems deployed inside a VirtualBox network using Host-only/NAT interfaces.



## ⚙️ Installation & Configuration

### 🧠 Wazuh SIEM Setup

```bash
# Clone Wazuh Docker deployment
git clone https://github.com/wazuh/wazuh-docker.git
cd wazuh-docker/single-node
docker-compose up -d
```

### 🛡️ Enroll Endpoint (Ubuntu/Debian Agent)

```bash
curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | sudo apt-key add -
echo "deb https://packages.wazuh.com/4.x/apt stable main" | sudo tee /etc/apt/sources.list.d/wazuh.list
sudo apt update
sudo apt install wazuh-agent
```

Edit agent config (`/var/ossec/etc/ossec.conf`) → Set Wazuh manager IP

```bash
sudo systemctl start wazuh-agent
sudo systemctl enable wazuh-agent
```

Enroll agent via Wazuh Web UI or CLI



### 🌐 ntopng Setup

```bash
sudo apt update
sudo apt install ntopng
sudo nano /etc/ntopng/ntopng.conf
```

Set monitored interface:
```
-i=enp0s3
```

Start service:
```bash
sudo systemctl restart ntopng
```

Access dashboard:  
→ `http://<your-ip>:3000`



## 🔬 Simulated Attacks

| Attack Type           | Tools Used     | Detection by Wazuh | Detected by ntopng |
|------------------------|----------------|---------------------|---------------------|
| SSH Brute Force        | Hydra          | ✅ Credential Access | ✅ High flow rate    |
| FTP Login Abuse        | Hydra          | ✅ Auth Fail Alerts  | ✅ FTP traffic spike |
| MySQL Exploitation     | Metasploit     | ✅ Suspicious Input  | ✅ MySQL flow burst  |
| SMTP Spoofing Attempt  | Swaks          | ✅ Untrusted Sender  | ✅ TCP/SMTP flag     |
| OS Scan / Recon        | Nmap           | ✅ Scan Rule Trigger | ✅ Port sweep log    |



## 📊 Wazuh Dashboard

- Alerts categorized by **MITRE ATT&CK** technique  
- Dashboard filters: Severity, IP, Geo-location, Rule ID  
- Custom rules added for brute-force detection and scan patterning  
- Agent status monitored in real-time



## 📈 ntopng Insights

- Top talkers, active flows, and alert history  
- Protocol distribution (HTTP, SSH, FTP, DNS)  
- Flow geolocation and anomaly detection  
- Suspicious connection patterns flagged visually



## 📎 Screenshots (Optional)

- [Wazuh MITRE Classification](#)  
- [ntopng Traffic Heatmap](#)  
- [Hydra Attack Logs](#)  
- [Kibana Alert View](#)



## 🧠 Lessons Learned

- Wazuh is flexible and powerful for alert correlation and endpoint monitoring  
- ntopng complements Wazuh with flow-level traffic insights  
- Docker-based deployment speeds up SIEM lab setup  
- Simulated attack patterns are essential for tuning rule sets  
- Combined SIEM + NSM strengthens detection and awareness capabilities



## 🧪 Tools Used

- 🧠 **Wazuh** – Log correlation and SIEM  
- 📈 **ntopng** – Network security monitoring  
- 🛠️ **Suricata** – IDS engine (optional add-on)  
- 🧪 **Hydra**, **Nmap**, **Metasploit**, **Swaks** – Attack simulators  
- 🔍 **Elasticsearch**, **Kibana**, **Docker Compose**



## 📎 GitHub Repository (Optional)

> [🔗 View Source Code or Configuration Files](https://github.com/oluwafemiab/siem-wazuh)



## 🧠 Final Thoughts

This SIEM system serves as a powerful baseline for building real-time, open-source monitoring environments. The integration of Wazuh and ntopng provides both **deep log analysis** and **broad network visibility**, making it suitable for small SOCs, academic labs, or SME infrastructure.



## 📬 Let’s Connect

If you’re building your own SIEM lab or exploring Wazuh and ntopng, feel free to reach out on [LinkedIn](https://www.linkedin.com/in/ajijola-oluwafemi-ba839712a).
