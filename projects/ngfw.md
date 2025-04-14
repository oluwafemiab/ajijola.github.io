# 🛡️ Building a Honeypot System with a Next-Generation Firewall (NGFW)

**Author:** Ajijola Oluwafemi Blessing  
**Tools Used:** Cowrie, Dionaea, IPFire, ELK Stack, Metasploit, Hydra, Kali Linux, Logstash, Elasticsearch, Kibana



## 🔍 Overview

In this project, I designed and deployed a **deception-based security system** by integrating **low and medium interaction honeypots (Cowrie and Dionaea)** with a **Next-Generation Firewall (IPFire)**. The goal was to simulate cyberattacks in a virtual lab, capture attacker behavior, and build a defense system that could **detect, analyze, and mitigate Advanced Persistent Threats (APTs)**.



## 🧱 Objectives

- Deploy honeypots that simulate real services like SSH, FTP, HTTP, MySQL, etc.  
- Route simulated attack traffic through a NGFW (IPFire) for filtering and visibility  
- Log all events and interactions  
- Analyze attack data using the ELK Stack (Elasticsearch, Logstash, Kibana)  
- Automate IP blocking using cronjobs and Suricata alerts



## 🔧 Tools & Architecture

**Honeypots:**  
- Cowrie → Emulates SSH and Telnet  
- Dionaea → Emulates FTP, SMB, HTTP, MySQL, etc.

**Firewall:**  
- IPFire → Open-source NGFW acting as a gateway between attacker and honeypots  
- Used to simulate real traffic inspection and rule-based blocking

**Log Management:**  
- Logstash → Parses `.log` and `.json` files  
- Elasticsearch → Stores and indexes honeypot logs  
- Kibana → Visualizes attacks by protocol, IP, port, and geo-location

**Attack Simulation Tools:**  
- Hydra  
- Metasploit  
- Gobuster  
- Swaks  
- Nmap



## 🌐 Network Topology

```
Attacker VM (Kali Linux)
        ↓
  [IPFire NGFW]
        ↓
  Honeypot VMs:
   - Cowrie (Ubuntu)
   - Dionaea (Debian)
```

All machines were isolated within a **virtual NAT environment** using VMware, with manual port redirection and custom firewall rules.



## 🔬 Key Features

- **Real-Time Log Ingestion:** Logs from Cowrie and Dionaea sent to Logstash and visualized with Kibana dashboards  
- **Service Emulation:** SSH, FTP, HTTP, MySQL, SMB, Telnet  
- **Mitigation Script:** Auto-block malicious IPs on IPFire based on Suricata logs via cronjob  
- **Visualization Examples:**  
  - Most attacked ports  
  - Attacker country (GeoIP)  
  - Failed login attempts (username/password combinations)



## 📊 Insights & Results

- Majority of brute-force attacks targeted SSH and MySQL  
- Cowrie provided detailed session logs and credentials used  
- Dionaea captured malware payload delivery attempts on SMB  
- IPFire effectively blocked repeat attackers based on real-time logs  
- Most attacks originated from public cloud IP ranges



## 🧠 Lessons Learned

- IPFire is lightweight and easy to integrate, but requires manual tuning for advanced use  
- ELK Stack is powerful but resource-intensive — optimize config for test environments  
- Cowrie is ideal for authentication-based monitoring; Dionaea adds multi-protocol depth  
- Honeypots must be isolated to prevent misuse



## 🧪 Tools Used

- 💻 **Cowrie** – SSH/Telnet honeypot  
- 🌐 **Dionaea** – FTP/SMB/HTTP honeypot  
- 🔥 **IPFire** – Next-Generation Firewall  
- 📊 **ELK Stack** – Log analysis and visualization  
- 🐍 **Hydra**, 🛠️ **Metasploit**, 🧪 **Swaks**, 🧵 **Gobuster**, 📡 **Nmap**



## 📎 GitHub Repository 

> [🔗 GitHub Deployment ](https://github.com/oluwafemiab/ngfw-honeypot-system)



## 🧠 Final Thoughts

This project gave me real-world experience in **deception technologies**, **network security**, and **log-driven threat analysis**. Honeypots combined with firewalls and logging platforms offer **affordable and powerful ways to study cyber threats**, especially for students and SMEs.



## 📬 Let’s Connect

If you're working on a similar project or want help setting up your own honeypot lab, feel free to reach out on [LinkedIn](https://www.linkedin.com/in/ajijola-oluwafemi-ba839712a).



