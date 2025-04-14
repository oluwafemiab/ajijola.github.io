# ✉️ Developing a Secure Email Gateway with Axigen & PGP Encryption

**Author:** Ajijola Oluwafemi Blessing  
**Tools Used:** Axigen Mail Server, PGP, GoPhish, Proxmox Mail Gateway, Thunderbolt, Swaks, SSL, VirtualBox



## 🔍 Overview

This project focused on designing and deploying a **secure email infrastructure** to protect against phishing, spoofing, and unauthorized access. The system was tailored for **SMEs**, integrating **PGP encryption**, **anti-spam**, and **phishing simulation** tools within a layered gateway setup.

The goal was to demonstrate how small organizations can implement robust email protection without relying on expensive commercial products.



## 🧱 Objectives

- Set up a fully functional mail server using Axigen  
- Enable secure email communication using PGP encryption (Thunderbird + Enigmail)  
- Simulate phishing attacks using GoPhish for user awareness  
- Deploy a Proxmox Mail Gateway to filter spam, spoofed messages, and malware  
- Enforce HTTPS access and SSL certificates  
- Test email spoofing and open relay protection using Swaks



## 🔧 Tools & Architecture

**Mail Server:**  
- **Axigen Mail Server** – Provided webmail, IMAP/SMTP/POP3, and user management

**Security Layer:**  
- **Proxmox Mail Gateway** – Filtered spam, viruses, and policy violations  
- **PGP (Thunderbird + Enigmail)** – Used for end-to-end message encryption and verification  
- **GoPhish** – Used to simulate phishing attacks to test awareness

**Testing Tools:**  
- **Swaks** – Tested for open relay vulnerabilities  
- **Thunderbird** – Mail client for PGP key handling  
- **SSL Certs** – Enabled HTTPS mail access and secured admin panels



## 🌐 Network Layout

```
Client Email (Thunderbird) --> Axigen Mail Server --> Proxmox Mail Gateway --> Internet
                                 ↓
                          GoPhish Server (Phishing Simulation)
```

All services were hosted on VirtualBox within an isolated NAT environment for safety and testing flexibility.



## 🔬 Key Features

- **Email Encryption:** Enabled PGP encryption and digital signatures for all outgoing/incoming emails  
- **Phishing Simulation:** Crafted fake campaigns to test awareness and display risks to users  
- **Spam Filtering:** Configured Proxmox Mail Gateway to identify spam, suspicious links, and spoofing attempts  
- **Access Control:** SSL-protected webmail and admin interfaces  
- **Open Relay Protection:** Verified via Swaks that no unauthorized sending was possible



## 📊 Results & Impact

- **Phishing tests** successfully bypassed standard user awareness until mitigated  
- Proxmox blocked 90% of spam and malformed messages  
- HTTPS encryption prevented data interception  
- PGP enabled full email integrity and confidentiality



## 🧠 Lessons Learned

- Many SME mail systems are vulnerable due to poor configuration  
- Open-source tools can provide enterprise-grade protection if configured correctly  
- Phishing simulations are essential for real training — awareness starts with visibility  
- SSL and DNS (SPF, DKIM, DMARC) are critical to trust and delivery



## 🧪 Tools Recap

- 📨 **Axigen** – Core mail server  
- 🔐 **PGP + Enigmail** – Email encryption  
- 🧪 **Swaks** – Open relay and spoofing test  
- 🦠 **Proxmox Mail Gateway** – Spam and virus filter  
- 🧠 **GoPhish** – Awareness simulation  
- 🛡️ **Thunderbird** – PGP mail client  
- 🔒 **SSL** – HTTPS admin and user portals



## 📎 GitHub Repository (Optional)

> [🔗 View Configurations or Deployment Notes](https://github.com/oluwafemiab/email-security-gateway/)



## 🧠 Final Thoughts

This project proved that **secure email systems are achievable** even for small organizations with limited resources. With proper configuration and layered defenses, threats like phishing and spoofing can be dramatically reduced.



## 📬 Let’s Connect

If you're interested in email security, PGP, or phishing simulations, feel free to reach out on [LinkedIn](https://www.linkedin.com/in/ajijola-oluwafemi-ba839712a).

---
