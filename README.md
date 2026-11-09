# Footprint-Scanning-B084
Learning about information gathering through Scanning 

# Footprinting & Network Scanning: Penetration Testing Report

A hands-on penetration testing project covering the first two phases of an engagement: **Reconnaissance & Footprinting** and **Scanning & Network Discovery**, performed with Kali Linux tools and Zenmap.

> **Disclaimer:** All activities were performed only on systems where I had written permission (the target provided by my program) and on my own local network. This repository is for education and research. Do not use anything here against systems you do not own or have authorisation to test.

## Project Overview

| | |
|---|---|
| **Pentester** | Alabi Abdulhameed Ayomikun |
| **Program / Batch** | B084 |
| **Date** | 08 November 2026 |
| **Modules** | W2-PM1 (Multiple Kali Tools), W2-PM5 (Zenmap Scanning) |
| **Targets** | 1. networkwalks.com (permission secured in writing) 2. My own local LAN |
| **Phases covered** | Phase 1: Reconnaissance & Footprinting, Phase 2: Scanning & Network Discovery |

## Tools Used

| Tool | Purpose |
|---|---|
| WHOIS | Domain registration details (owner, dates, name servers) |
| WhatWeb | Fingerprint web technologies (server, CMS, plugins, IP) |
| nslookup | Resolve the domain name to its IP address |
| curl -I | Read HTTP response headers |
| wafw00f | Detect whether a Web Application Firewall protects the site |
| DNSRecon | Enumerate DNS records (NS, MX, SPF, TXT, SRV) |
| Zenmap (Nmap GUI) | Scan the local subnet for live hosts, IPs and MAC addresses |
| ipconfig | Identify local IP and subnet on Windows |

## Phase 1: Reconnaissance & Footprinting

Run from Kali Linux against the target domain:

```bash
whois networkwalks.com
whatweb networkwalks.com
nslookup networkwalks.com
curl -I https://networkwalks.com
wafw00f https://networkwalks.com
dnsrecon -d networkwalks.com
```

**Key findings:**
- Target IP address: 192.232.216.135.
- Technologies identified: WordPress 7.1.4 and WP Download Manager 3.3.76
- Web Application Firewall:  ModSecurity (SpiderLabs)
- DNS records exposed: hostgator.com, mail.networkwalks.com, networkwalks.com

## Phase 2: Network Scanning with Zenmap

1. Found my local IP and subnet with `ipconfig`.
2. Entered the subnet in Zenmap and ran a **Ping Scan** to identify live hosts.
3. Recorded each host's IP and MAC address.
4. Used the **Topology** tab to view the network map and exported the result as a PDF.

**Live host found:** 1, 192.168.56.1

## Risk Analysis Summary

| # | Finding | Risk |
|---|---|---|
| 1 | Web technology and version information exposed | Medium |
| 2 | Server IP identifiable | Low |
| 3 | HTTP technical information exposed via headers | Low |
| 4 | WAF identifiable | Low |
| 5 | DNS infrastructure information exposed | Medium |


These are observations from information gathering and host discovery. No exploitation or vulnerability validation was performed.

## Recommendations

- Review what technology information is publicly exposed (versions, plugins).
- Hide or minimise HTTP headers that reveal server details.
- Review DNS records and remove anything unnecessary.
- Keep the WAF tuned and updated.
- Perform regular network scans of your own networks to find unknown devices.
- Document the network topology and keep it current.
- Keep software updated and test only with written authorisation.

## What I Learned

- Public information (DNS, headers, technologies) reveals a lot before any scan is run.
- How to move from passive footprinting to active scanning in a controlled way.
- Why authorisation and a clear scope come first in every engagement.
- How to turn raw tool output into a risk-based report with clear recommendations.

## Repository Contents

```
.
├── README.md
├── Report/
│   └── W2-PM-FINAL-Report.pdf
└── Screenshots/
    ├── whois.png
    ├── whatweb.png
    ├── nslookup-curl.png
    ├── wafw00f.png
    ├── dnsrecon.png
    ├── zenmap-scan.png
    └── zenmap-topology.png
```

## Author

**Alabi Abdulhameed Ayomikun** 
LinkedIn: https://www.linkedin.com/in/abdulhameed-alabi-866272342)
