# Day3 - Networking Basics

## What is DNS?
DNS converts a domain name into an IP address.
Think of it like a phone book — you know the name (google.com), DNS gives you the number (IP address), and your browser connects to that IP.

**Key Command**
```bash
nslookup google.com
```

**Why SOC Analysts Care**
- Malware uses DNS to call home to attacker servers
- SOC analysts monitor DNS logs to detect suspicious domains
- Unusual DNS queries = potential threat

**Common Mistakes**
- ❌ Thinking DNS converts IP → domain (it's the opposite)
- ❌ Ignoring DNS logs during investigations

---

## What is WHOIS?
WHOIS tells you who OWNS an IP address, what organization it belongs to, and what country it is from.

**Key Commands**
```bash
whois <IP address>
whois -h whois.arin.net <IP address>
```

**Regional Databases**
| Region | Database |
|--------|----------|
| North America | ARIN |
| Asia Pacific | APNIC |
| Europe | RIPE |
| Latin America | LACNIC |
| Africa | AfriNIC |

**Why SOC Analysts Care**
- Helps decide if an IP should be trusted
- Unknown organization + suspicious country = red flag
- Always check WHOIS during threat investigation

**Common Mistakes**
- ❌ Using wrong regional database
- ❌ Confusing "owns" with "hosts"

---

## What is a Port?
- IP address = hotel address
- Port = room number
- Each room handles a different type of service

**Key Ports to Memorize**
| Port | Protocol | Purpose |
|------|----------|---------|
| 21 | FTP | File transfer |
| 22 | SSH | Secure remote login |
| 25 | SMTP | Email sending |
| 53 | DNS | Domain name resolution |
| 80 | HTTP | Web traffic (unsecured) |
| 110 | POP3 | Email receiving |
| 143 | IMAP | Email receiving (synced) |
| 443 | HTTPS | Web traffic (secured) |
| 587 | SMTP | Email submission (secure) |
| 3389 | RDP | Remote desktop |
| 4444 | Metasploit | Almost always malicious |

**Key Commands**
```bash
ss -tulnp
ss -tulnp | grep ":80"
```

**Why SOC Analysts Care**
- Open ports = potential attack surface
- Unexpected open ports = immediate investigation
- Port 4444 open = escalate immediately

**Common Mistakes**
- ❌ Confusing IMAP 143 with SMTP 587
- ❌ Blocking suspicious ports immediately without investigating first

---

## HTTP vs HTTPS

| Port 80 HTTP | Port 443 HTTPS |
|--------------|----------------|
| Plain text | Encrypted |
| No certificate needed | Requires SSL certificate |
| Anyone can read traffic | Traffic is protected |

Think of it like this:
- Port 80 = Sending a postcard (anyone can read it)
- Port 443 = Sending a sealed locked envelope

**Common Mistakes**
- ❌ Thinking you can just switch port 80 to 443 without an SSL certificate

---

## SOC Response Process

> When I see something suspicious, I must first OBSERVE, then DOCUMENT, then ESCALATE.

```
1. OBSERVE    → Confirm what you are seeing is real
2. DOCUMENT   → Write down IP, port, time, machine name
3. ESCALATE   → Report to senior analyst
4. CONTAIN    → Team isolates the machine
5. BLOCK      → Block after evidence is collected
```

**Common Mistakes**
- ❌ Blocking immediately = destroys evidence + alerts attacker
- ✅ Junior SOC role = Detect, Document, Escalate

---

## Quick Reference — All Commands

| Skill | Command |
|-------|---------|
| Find IP of a domain | `nslookup google.com` |
| Find who owns an IP | `whois <IP>` |
| Check specific registry | `whois -h whois.arin.net <IP>` |
| List open ports | `ss -tulnp` |
| Filter specific port | `ss -tulnp \| grep ":port"` |
