# CIS Benchmark Level 1 Scan Using OpenSCAP

This document explains the complete process of installing OpenSCAP and performing
a CIS Benchmark Level 1 compliance scan on a Linux (Ubuntu) system.

---

## Step 1: Update the System

```bash
sudo apt update && sudo apt upgrade -y
```
---

## Step 2: Install OpenSCAP and Security Guide

```bash
sudo apt install -y openscap-scanner scap-security-guide

```

---

#### Explanation:
openscap-scanner → core SCAP scanning tool
scap-security-guide → provides CIS benchmark profiles
scap-Security-Guide(ssg) installs the benchmark XML files here: /usr/share/xml/scap/ssg/content/scap-security-guide-0.1.69/
e-0.1.69/ 
---
 
## Step 3: Verify OpenSCAP Installation

```bash 
oscap --version

```

 Confirms that OpenSCAP is installed correctly.
---

## Step 4: Locate CIS Benchmark Content

```bash 
cd  /usr/share/xml/scap/ssg/content/scap-security-guide-0.1.69/

ls /usr/share/xml/scap/ssg/content/scap-security-guide-0.1.69/
```
---
Explanation:
This directory contains SCAP data streams including CIS benchmarks

Example Files :
ssg-ubuntu2204-ds.xml,ssg-ubuntu2004-ds.xml .
Since my machine is Ubuntu 22.04, the correct SCAP file is ssg-ubuntu2204-ds.xml
---

## Step 5: Identify Available CIS Profiles

```bash 

oscap info ssg-ubuntu2204-ds.xml | less

```
---

Scroll slowly. You will see profiles like:

cis_level1_server
cis_level1_workstation
cis_level2_*

For this project, we use Level 1 Server (industry safe + beginner friendly).
Press q to exit.

---
## Step 6: Run the CIS Level 1 scan (MAIN COMMAND)

```bash 

sudo oscap xccdf eval \
--profile xccdf_org.ssgproject.content_profile_cis_level1_server \
--results cis-results.xml \
--report cis-report.html \
ssg-ubuntu2204-ds.xml
```
This may take 2–5 minutes
---

## Step 7: Confirm the files were created

After it finishes, run:

```bash 

ls -lh cis-report.html cis-results.xml
```

You should see file sizes (MBs), not zero bytes.
---

## Step 8: : Open the CIS report (Snap-safe method)

Because of Ubuntu 22.04 Firefox Snap issue, do this:

```bash 

sudo cp cis-report.html /home/me/
sudo chown me:me /home/me/cis-report.html
```

---

Now open it:
```bash 

firefox /home/me/cis-report.html
```

This will open the CIS report in the browser.
---

Inorder to open the CIS Level 1 Report  anytime, Use this command,(From the security-scan-guide-0.0.69/)

```bash 
xdg-open cis-report.html
```

## Conclusion

The CIS Benchmark Level 1 scan was successfully performed using OpenSCAP.
The system’s compliance status was evaluated and documented using standard CIS benchmarks.
---



