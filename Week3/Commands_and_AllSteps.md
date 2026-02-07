# CIS Benchmark Level 1 Scan Using OpenSCAP

This guide explains how to install OpenSCAP and perform a CIS Benchmark Level 1 compliance scan on Ubuntu 22.04.

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

**Explanation**  
- `openscap-scanner` → core SCAP scanning tool  
- `scap-security-guide` → provides CIS benchmark profiles  
- Benchmark XML files are installed under:  
  `/usr/share/xml/scap/ssg/content/scap-security-guide-0.1.69/`

---

## Step 3: Verify OpenSCAP Installation

```bash
oscap --version
```

Confirms that OpenSCAP is installed correctly.

---

## Step 4: Locate CIS Benchmark Content

```bash
ls /usr/share/xml/scap/ssg/content/scap-security-guide-0.1.69/
```

This directory contains SCAP data streams including CIS benchmarks.

Example files:  
- `ssg-ubuntu2204-ds.xml`  
- `ssg-ubuntu2004-ds.xml`

Since the system is Ubuntu 22.04, the correct file is:

```
ssg-ubuntu2204-ds.xml
```

---

## Step 5: Identify Available CIS Profiles

```bash
oscap info ssg-ubuntu2204-ds.xml | less
```

Profiles include:

- `cis_level1_server`
- `cis_level1_workstation`
- `cis_level2_*`

For this project, use **Level 1 Server**.  
Press `q` to exit.

---

## Step 6: Run the CIS Level 1 Scan

```bash
sudo oscap xccdf eval \
--profile xccdf_org.ssgproject.content_profile_cis_level1_server \
--results cis-results.xml \
--report cis-report.html \
ssg-ubuntu2204-ds.xml
```

This may take 2–5 minutes.

---

## Step 7: Confirm the Files Were Created

```bash
ls -lh cis-report.html cis-results.xml
```

You should see non‑zero file sizes.

---

## Step 8: Open the CIS Report (Snap‑Safe Method)

Ubuntu 22.04 Firefox Snap cannot open local files directly, so copy the report:

```bash
sudo cp cis-report.html /home/me/
sudo chown me:me /home/me/cis-report.html
```

Open it:

```bash
firefox /home/me/cis-report.html
```

---

## Step 9: Open the CIS Report Anytime

```bash
xdg-open cis-report.html
```

---

## Conclusion

The CIS Benchmark Level 1 scan was successfully performed using OpenSCAP.  
The system’s compliance status was evaluated and documented using standard CIS benchmarks.

---
