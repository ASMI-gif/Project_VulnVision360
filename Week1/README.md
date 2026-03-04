

# Week 1 Findings – Discovery & Attack Surface Mapping

## Objective
Perform internal network discovery and build a complete asset inventory with OS/service fingerprinting.

## Subnet Scanned
- 192.168.48.0/24

## Key Results
- Identified all live hosts in the subnet
- Performed OS detection and service version enumeration
- Documented open ports and exposed services
- Created a structured asset inventory table with risk zoning

## Discovered Assets (Inventory Summary)

| Asset IP        | Hostname         | OS / Device Type                     | Open Ports (Top)                         | Key Services Detected                          | Risk Zone |
|----------------|------------------|--------------------------------------|------------------------------------------|------------------------------------------------|----------|
| 192.168.48.1   | Unknown          | Windows (Server / 10 / 11)           | 80, 135, 445, 2179, 3306, 3389           | IIS HTTP, MSRPC, SMB, MySQL, RDP               | Internal Critical |
| 192.168.48.2   | VMware-NAT       | VMware Virtual Network Device        | 53                                       | DNS (dnsmasq)                                  | Internal Infrastructure |
| 192.168.48.129 | Windows-Server   | Windows Server 2016                  | 3389, 5985                               | RDP, WinRM                                      | Internal Critical |
| 192.168.48.131 | Metasploitable   | Linux 2.6 (Ubuntu / Metasploitable)  | 21,22,23,25,53,80,139,445,3306,8180,etc. | FTP, SSH, Telnet, SMTP, DNS, Samba, MySQL, Tomcat | Legacy / Unpatched (High Risk) |
| 192.168.48.254 | VMware-Gateway   | VMware Gateway / Network Adapter     | None                                     | None                                            | Low Risk / Internal |

## High Risk Observations
- Metasploitable (192.168.48.131) exposes multiple insecure legacy services such as:
  - FTP (21)
  - Telnet (23)
  - SMB (139/445)
  - Java RMI (1099)
  - Tomcat (8180)
  - MySQL (3306)
- Windows hosts expose remote management ports such as:
  - RDP (3389)
  - WinRM (5985)
- SMB exposure across Windows assets increases lateral movement risk.

## Attack Surface Summary
- Total Hosts Identified: 5
- High Risk Host: Metasploitable (Legacy / unpatched services)
- Critical Infrastructure Hosts: Windows Server + Windows endpoint

## Gate Check
✅ Asset discovery completed and internal attack surface mapped successfully.
