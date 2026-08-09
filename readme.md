# Nmap Network Discovery 
## Overview
This project demonstrates the use of Nmap for network discovery, port scanning, and service enumeration in an authorized lab environment.
## Lab Environment 
- Operating System: Windows
- Tool: Nmap
- Environment Home Network
## Objectives
- Verify Nmap installation
- Discover active hosts
- Identitfy open ports
- Detect running services
- Understand basic network enumeration

## Nmap Installation Verification
![Nmap Version](screenshots/01-nmap_version.png)
<p align ='center'>
  01-nmap_version.png
</p>

### Command
```bash
nmap --version
```

### Observation
- Verified that nmap was installed successfully.
- The installed version and supported libaries were displayed.
- The tool is ready for network scanning tasks.

### Why is this important?
- Verifying the installation ensure that Nmap is correctly configured before performing any scans.
- It confirms that the required components are available.
### What I Learned
- How to verify a successful Nmap installation.
- How to check installed version from the command line.

## Hosts Discovery

![Hosts Discovery](screenshots/02-hosts_discovery.png)
<p align ="center">
  02-hosts_discovery.png
</p>

## Command
```bash
nmap -sn -n 192.168.23.0/24
```

## What it does
Finds all live devices on the `192.168.23.0/24` network without scanning ports.

## Parameters

| Flag | Meaning |
|------|---------|
| `-sn` | Only checks which hosts are up (no port scan) |
| `-n` | Skips DNS lookup, makes scan faster |
| `192.168.23.0`| Target IP of subnet mask |
| `/24` | Scans the whole subnet (192.168.1.0–255), not just `.1` |

## Observation
- Output shows only **IP + MAC address** of live hosts (no ports/services/dns, since `-sn` & `-n` skips that).

## Why is this Important?
- Host discovery is always the **first step** before any port/service scan — no point scanning ports on a dead IP.
- ARP works at Layer 2, so it's more reliable than ping on a local network.
- This connects to Wireshark too — the ARP requests from this scan show up live with:

## What I Learned
- How Nmap performs basic host discovery.
- How to interpret `Host is up` in Nmap output.
- How CIDR notation such as `/24` defines a network range.
- How the `-sn` option focuses the scan on host discovery.
- How the `-n` option disables DNS resolution.
