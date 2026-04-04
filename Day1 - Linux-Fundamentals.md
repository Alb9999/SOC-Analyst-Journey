# 📅 Day 1 — Linux Fundamentals
> **Date:** 2026-03-28
> **Phase:** 1 — Linux Fundamentals
> **Status:** ✅ Completed

---

## 🎯 What I Learned Today

- How the Linux filesystem is structured
- How to navigate using the terminal
- How to read and investigate log files
- What permissions mean and why they matter
- How to detect suspicious activity in auth.log

---

## 🗂️ Linux Filesystem — The Big Picture

Everything in Linux starts from one root `/`

```
/                   ← Root (the lobby)
├── etc/            ← Configuration files
├── var/
│   └── log/        ← LOGS — your #1 investigation spot
├── home/
│   └── albert/     ← My personal folder
├── tmp/            ← Temp files — attackers drop malware here
├── bin/            ← Basic system commands
└── root/           ← Home folder for root (admin) user
```

### SOC Relevance

| Folder | Why it matters |
|---|---|
| `/var/log/` | All system activity is recorded here |
| `/etc/` | Attackers modify config files to persist |
| `/tmp/` | Writable by anyone — common malware drop point |
| `/home/` | User files — suspicious files here = red flag |
| `/root/` | If attacker reaches here, system is fully compromised |

---

## ⌨️ Commands Learned

### Navigation
```bash
pwd               # Show current directory
ls                # List files in current folder
ls -la            # List ALL files including hidden + show permissions
cd /var/log       # Navigate to log folder
cd ..             # Go up one level
cd ~              # Go to home folder
```

### Reading Files
```bash
cat auth.log              # Read entire file
sudo cat auth.log         # Read protected file as admin
tail auth.log             # Show last 10 lines
tail -f auth.log          # Live view — updates in real time
grep "Failed" auth.log    # Search for specific keyword
```

### Chaining Commands
```bash
grep "Failed" auth.log | grep "10.0.0.5"
# Find lines with "Failed" AND a specific IP address
```

---

## 🔐 Permissions Explained

```
drwxr-xr-x  albert  albert  documents/
│ │││ │││ │││
│ │││ │││ └── Others: read + execute
│ │││ └────── Group: read + execute
│ └────────── Owner: read + write + execute
└──────────── d = directory, - = file
```

| Symbol | Meaning |
|---|---|
| `r` | Read |
| `w` | Write |
| `x` | Execute |
| `-` | No permission |

---

## 🔴 SOC Scenarios Practiced

### Scenario 1 — Investigating a Suspicious Login

```bash
cd /var/log
sudo grep "Failed" auth.log      # Check for brute force attempts
sudo grep "Accepted" auth.log    # Check for successful logins
sudo tail -f auth.log            # Watch live activity
```

**Observation → Meaning → Conclusion:**
- Observation: 847 failed passwords then 1 accepted login at 2:47 AM
- Meaning: Brute force attack succeeded
- Conclusion: Account is compromised — escalate immediately

### Scenario 2 — Live Monitoring

Ran `sudo tail -f auth.log` in Terminal 1.
Ran `sudo apt update` in Terminal 2.
Watched Terminal 1 catch the sudo command **in real time.**

**Key lesson:** Every sudo action is logged instantly.
Attackers cannot hide their commands unless they delete the logs.
And deleting logs is itself a red flag.

---

## 💡 Key Takeaways

1. Always use `ls -la` not `ls` — attackers hide files with a `.` prefix
2. `/var/log/auth.log` is your #1 file for login investigation
3. `sudo` commands are always logged — this is how attackers get caught
4. `tail -f` is your live CCTV during an active incident
5. `grep` is your flashlight — search large log files for specific events
6. `Permission denied` = add `sudo`, then ask why the file is protected

---

## ✅ Lab Completed

- [x] Opened Ubuntu terminal
- [x] Ran `pwd` — confirmed location `/home/albert`
- [x] Ran `ls` and `ls -la` — discovered hidden files and permissions
- [x] Navigated to `/var/log`
- [x] Read `auth.log` with sudo
- [x] Used `grep` to search for failed and accepted logins
- [x] Used `tail -f` to watch live system activity
- [x] Observed real-time sudo logging in action

---

## 📝 Homework

Run these 5 commands from memory — no notes:
```bash
pwd
ls -la
cd /var/log
sudo tail auth.log
sudo grep "Failed" auth.log
```

---


