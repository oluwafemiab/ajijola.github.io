# 🧪 Comparative Honeypot Analysis: MySQL-HoneypotD, HoneyDB, and Heralding

**Author:** Ajijola Oluwafemi Blessing  
**Tools Used:** MySQL-HoneypotD, HoneyDB, Heralding, ELK Stack (Logstash, Elasticsearch, Kibana), Hydra, Nmap, Gobuster, Swaks, Kali Linux, Debian, Ubuntu



## 🔍 Overview

This project presents a comparative evaluation of three open-source honeypots — **MySQL-HoneypotD**, **HoneyDB**, and **Heralding** — under simulated attack conditions. The goal was to assess their effectiveness in **detecting attacks**, **service emulation coverage**, **log richness**, and **ease of deployment**. Logs from each honeypot were normalized using the ELK Stack and visualized for deeper analysis.



## 🧱 Objectives

- Deploy and configure each honeypot in isolated virtual machines  
- Simulate a variety of attacks (brute-force, enumeration, phishing, etc.)  
- Normalize logs and visualize threat data using ELK Stack  
- Analyze detection performance, service coverage, and logging quality  
- Recommend the most suitable honeypot based on real-world threat simulation



## 🔧 Tools & Configuration

**Honeypots Deployed:**  
- **MySQL-HoneypotD:** Simulates MySQL services for brute-force and enumeration  
- **HoneyDB:** Emulates low-interaction services like FTP, HTTP, SSH, SNMP  
- **Heralding:** High-interaction honeypot supporting over 15 protocols including SSH, RDP, Telnet, MySQL, LDAP, SIP

**Attack Tools Used:**  
- Hydra (SSH, FTP, MySQL brute-force)  
- Nmap (service scan, OS fingerprinting)  
- Gobuster (directory brute-forcing)  
- Swaks (SMTP testing and relay abuse simulation)

**Log Analysis & Visualization:**  
- **Logstash** → Ingests `.log`, `.json`, `.csv` files from all honeypots  
- **Elasticsearch** → Stores, indexes, and structures logs  
- **Kibana** → Visualizes data: protocol heatmaps, service frequency, attacker IPs



## 🧪 Attack Simulation Coverage

| Protocol/Service | Tools Used       | Honeypots Tested          | Attack Type                |
|------------------|------------------|----------------------------|----------------------------|
| SSH              | Hydra            | HoneyDB, Heralding         | Brute-force login attempts |
| FTP              | Hydra, Medusa    | HoneyDB, Heralding         | Password guessing          |
| MySQL            | Hydra, Nmap      | MySQL-HoneypotD, Heralding | Login attempts, scans      |
| HTTP             | Gobuster, Curl   | HoneyDB, Heralding         | Directory enumeration      |
| SMTP             | Swaks            | Heralding                  | Open relay/phishing test   |
| POP3/IMAP        | Hydra            | Heralding                  | Credential brute-force     |
| SNMP             | onesixtyone      | HoneyDB                    | String guessing            |
| RDP              | Hydra            | Heralding                  | Remote login attack        |



## 🌐 Network Topology

```
Attacker VM (Kali Linux)
        ↓
    [Bridged NAT]
        ↓
 Honeypot VMs:
  - MySQL-HoneypotD
  - HoneyDB
  - Heralding
```

All traffic was isolated within a NAT environment using VMware Workstation.



## 🔬 Detection & Logging

- **Heralding** produced rich JSON/CSV logs with full session replay  
- **HoneyDB** used simple structured logs, covering multiple ports  
- **MySQL-HoneypotD** provided raw `.log` output specific to MySQL activity  
- ELK Stack helped visualize and normalize attack types and frequency



## 📊 Insights & Evaluation

| Metric                     | MySQL-HoneypotD | HoneyDB          | Heralding         |
|----------------------------|-----------------|------------------|-------------------|
| Protocols Emulated         | 1 (MySQL)       | ~5               | 15+               |
| Log Format                 | Plaintext       | Structured Logs  | JSON, CSV         |
| Ease of Deployment         | High            | High             | Medium            |
| Log Detail Quality         | Basic           | Good             | Very High         |
| Ideal Use Case             | DB brute-force  | Lightweight trap | Credential trap   |

**Key Takeaways:**
- **Heralding** is best for broad protocol coverage and authentication trap setups  
- **HoneyDB** is suitable for lightweight multi-service deployments  
- **MySQL-HoneypotD** is ideal for targeted database trap environments



## 📎 Log Examples (Normalized in ELK)

- SSH brute-force attempts with credentials captured  
- MySQL login scans with detected IPs  
- HTTP directory brute-forcing (Gobuster paths)  
- SMTP phishing payload sent and flagged  
- Port scan logs visualized with heatmaps in Kibana



## 📂 File Formats Captured

| Honeypot         | Log File                     | Format     |
|------------------|------------------------------|------------|
| MySQL-HoneypotD  | `honeypotdsavedlog.log`      | Plaintext  |
| HoneyDB          | `ftp.log`, `ntp.log`, etc.   | JSON       |
| Heralding        | `log_session.json`, `auth.csv` | JSON, CSV |



## 🧠 Lessons Learned

- High-interaction honeypots provide better insight but require stronger isolation  
- ELK Stack is an essential component for real-time threat visibility  
- Using multiple honeypots increases detection coverage across protocols  
- Proper parsing and field extraction in Logstash is key to unified analysis



## 🧪 Tools Used

- 🐍 **Hydra** – Brute-force tool  
- 🧵 **Gobuster** – Directory scanner  
- 🐙 **Swaks** – SMTP test tool  
- 📊 **ELK Stack** – Log processing and visualization  
- 🛡️ **MySQL-HoneypotD**, **HoneyDB**, **Heralding** – Deception tools  
- 🧪 **Kali Linux**, **Debian**, **Ubuntu** – VM environments for testing



## 📎 GitHub Repository (Optional)

> [🔗 View Source Code or Config Files](https://github.com/oluwafemiab/honeypot-comparison)



## 🧠 Final Thoughts

Running a comparative honeypot analysis deepened my understanding of attacker behavior, logging challenges, and tool configuration. It also helped highlight the trade-offs between ease of deployment and log richness. Combined with ELK, this setup acts as a strong foundation for threat detection labs and research-driven SOC training.



## 📬 Let’s Connect

If you're interested in honeypots, ELK Stack, or deception-based detection systems, feel free to connect on [LinkedIn](https://www.linkedin.com/in/ajijola-oluwafemi-ba839712a).
