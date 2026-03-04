# VulnVision 360 – Continuous Compliance & Threat Exposure Engine

## Overview
**VulnVision 360** is a vulnerability management + compliance automation project designed to simulate how security teams continuously identify, prioritize, and remediate risks in an internal enterprise network.

This project focuses on both **threat exposure detection (vulnerabilities)** and **configuration compliance (CIS benchmarks)**, with structured documentation and evidence reports.

---

## Key Capabilities
This project performs:

- **Network discovery & asset inventory** (Nmap scanning)
- **Attack surface mapping** (open ports + services)
- **Vulnerability assessment** (OpenVAS/GVM authenticated & unauthenticated scans)
- **CVE analysis & prioritization** (Critical CVEs and exploit research)
- **Compliance auditing** (OpenSCAP CIS Benchmark scanning)
- **OVAL-based vulnerability checks** (Canonical Ubuntu security metadata)
- **Automated remediation planning** (Ansible playbooks - Week 4)
- **Closed-loop validation** (before/after rescans)

---

## Tools Used
- Nmap
- OpenVAS / GVM (Greenbone Vulnerability Manager)
- OpenSCAP (oscap)
- Canonical Ubuntu OVAL Feeds
- Ansible
- Linux Bash Automation
- GitHub Documentation + Evidence Reports

---

## Lab Environment
- **Scanner Machine:** Kali Linux
- **Linux Target:** Metasploitable2 (SSH Auth Scan + Vulnerability Testing)
- **Compliance Target:** Ubuntu 22.04 (OpenSCAP CIS + OVAL Scan)
- **Windows Target:** Windows Server (SMB/RDP exposure testing)

---

## Project Workflow (4-Week Plan)

### ✅ Week 1: Discovery & Asset Inventory
- Identified live hosts in internal subnet
- Performed OS detection + service fingerprinting
- Built asset inventory table with risk zones

📌 Output:
- Nmap scan evidence
- Asset inventory documentation

---

### ✅ Week 2: Vulnerability Assessment (Auth vs Unauth)
- Ran unauthenticated OpenVAS scan (external attacker view)
- Ran authenticated scan (internal view using SSH/SMB credentials)
- Extracted and documented at least one **Critical CVE (CVSS 9+)**
- Created Auth vs Unauth comparison table

📌 Output:
- Vulnerability scan reports
- Critical CVE analysis documentation

---

### ✅ Week 3: Compliance Automation (OpenSCAP)
- Installed OpenSCAP on Ubuntu compliance target
- Ran **CIS Level 1 Server Benchmark scan**
- Generated structured compliance reports (**HTML + XML**)
- Identified configuration failures (SSH hardening, password policy, firewall, audit rules)
- Performed Canonical OVAL vulnerability evaluation

📌 Output:
- CIS compliance report + results
- OVAL vulnerability report + results
- Week 3 compliance findings documentation

---

### ⏳ Week 4: Remediation + Rescan Validation (In Progress)
- Apply remediation using Ansible hardening playbooks
- Patch vulnerable packages / fix misconfigurations
- Re-run OpenVAS and OpenSCAP scans
- Compare results before vs after remediation

📌 Output:
- Ansible remediation scripts
- Validation scan reports
- Before/After dashboard improvements

---

## Reports & Evidence
All reports, scan outputs, screenshots, and weekly documentation are stored inside:

- `docs/`
- `week1-discovery/`
- `week2-vulnerability-assessment/`
- `week3-compliance-automation/`
- `dashboard/`

---

## Goal
The final objective of VulnVision 360 is to deliver a complete **continuous security pipeline** that maps assets, identifies vulnerabilities, checks compliance, automates remediation, and validates improvements with measurable results.
