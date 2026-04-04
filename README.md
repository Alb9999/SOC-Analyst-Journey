# 🛡️ SOC-Analyst-Journey
> Documenting my transition from IT Support to SOC Analyst — one day at a time.

---

## 👤 About Me
- 🖥️ Background: IT Support (hardware, troubleshooting)
- 🌱 Currently learning: CompTIA A+, Linux, Networking
- 🎯 Goal: Become a job-ready SOC Analyst
- 📍 Started: March 2026

---

## 🎯 What This Repo Is
This is my personal SOC analyst training journal.
Every day I learn, practice, and document:
- New concepts explained in simple terms
- Real commands I ran in my lab
- SOC scenarios and how to investigate them
- Key takeaways and lessons learned

This is not a textbook. This is real hands-on learning from zero.

---

## 🗺️ Training Roadmap

| Phase | Topic | Status |
|---|---|---|
| Phase 1 | Linux Fundamentals | ✅ Complete |
| Phase 2 | Networking (TCP/IP, DNS, Ports) | ✅ Complete |
| Phase 3 | SOC Skills (Logs, SIEM, Detection) | ✅ Complete |
| Phase 4 | Offensive Basics (Attacker Mindset) | 🟡 In Progress |

---

## 📂 Training Log

| Day | Topic | Notes |
|---|---|---|
| Day 1 | Linux Fundamentals | Filesystem, logs, permissions, auth.log investigation |
| Day 2 | Process Monitoring | ps, ps aux, top, grep filtering |
| Day 3 | Networking Basics | DNS, WHOIS, Ports, HTTP vs HTTPS, SOC Response Process |
| Day 4 | Network Scanning | nmap, netdiscover, nbtscan, banner grabbing, CVE hunting |
| Day 5 | Log Analysis | auth.log, ufw.log, brute force detection, O-M-C method |
| Day 6 | SIEM Introduction & Wazuh Setup | SIEM concepts, Wazuh installation, agent deployment |
| Day 7 | Wazuh Dashboard & Event Analysis | MITRE ATT&CK, Windows Event IDs, alert investigation |
| Day 8 | Attacker Mindset & Offensive Security Basics | Attacker types, path of least resistance, APT vs opportunistic, SOC detection thinking |

---

## 🧰 Lab Setup
- OS: Ubuntu 22.04 LTS (6GB RAM)
- Platform: Oracle VirtualBox (local VM)
- Tools: Terminal, grep, tail, nslookup, whois, ss, nmap, netdiscover, nbtscan
- SIEM: Wazuh 4.11.2 (self-hosted)
- Agent: Wazuh Agent on Windows PC

---

## 💡 How I Study
1. Hands-on first — I type every command myself
2. Understand the WHY before memorizing the HOW
3. Apply SOC thinking: **Observation → Meaning → Conclusion**
4. Document everything here

---

## 📈 Progress Tracker

- [x] Set up Ubuntu VM
- [x] Learned Linux filesystem structure
- [x] Navigated and read real log files
- [x] Investigated auth.log for suspicious activity
- [x] Used tail -f for live log monitoring
- [x] Process monitoring (ps, top, netstat)
- [x] DNS — domain to IP resolution
- [x] WHOIS — IP ownership lookup
- [x] Port analysis — ss -tulnp
- [x] HTTP vs HTTPS — port 80 vs 443
- [x] SOC Response Process — Observe, Document, Escalate
- [x] Network scanning with nmap
- [x] Banner grabbing and CVE hunting
- [x] Local network discovery — netdiscover
- [x] Finding hidden Windows devices — nmap -Pn
- [x] Device investigation — nbtscan + MAC lookup
- [x] Port 445 SMB and WannaCry
- [x] Unknown port investigation process
- [x] Log analysis — auth.log and ufw.log
- [x] Brute force attack detection
- [x] O-M-C investigation method
- [x] Suspicious login detection
- [x] Incident report writing
- [x] SIEM concepts — collection, normalization, correlation
- [x] Alert types — True/False Positive and Negative
- [x] Wazuh installation on Ubuntu VM
- [x] Wazuh agent deployment on Windows
- [x] Wazuh dashboard exploration
- [x] MITRE ATT&CK tactics and techniques
- [x] Windows Event IDs and Logon Types
- [x] Real event investigation in Wazuh
- [x] Attacker mindset — think like the enemy
- [x] Path of least resistance — how attackers choose targets
- [x] Opportunistic vs APT attacker types
- [x] SOC detection thinking — quiet signals vs loud alerts
- [x] Basic IP investigation — VirusTotal, AbuseIPDB, Whois
- [ ] Cyber Kill Chain
- [ ] Advanced threat hunting
- [ ] Writing SOC incident reports

---

*This repo is updated after every training session.*
*From IT Support → SOC Analyst. Let's go. 🔥*
