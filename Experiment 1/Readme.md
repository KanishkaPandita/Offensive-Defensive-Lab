# Experiment 1: Scanning for Vulnerabilities in a Network

## Overview

This experiment focuses on identifying active hosts, open ports, running services, and known security vulnerabilities in a target network using **Nmap** and **Nessus**. Nmap is used for network discovery and service detection, while Nessus is used to perform vulnerability assessment and identify potential security risks.

## Objective

To identify active hosts, open ports, running services, and known vulnerabilities on a target network using Nmap and Nessus.

## Tools and Technologies Used

- **Kali Linux** – Attacker and scanning machine.
- **Nmap** – Network discovery and port scanning.
- **Nessus** – Vulnerability assessment tool.
- **Target Machine** – Authorized system used for security testing.

## Methodology

### Step 1: Check IP Address and Connectivity

Check the IP address of the Kali Linux machine and verify connectivity with the target machine.

```bash
ifconfig
ping <target-ip>
```

### Step 2: Discover Live Hosts

Perform a ping scan to identify active devices on the network.

```bash
nmap -sn 192.168.56.0/24
```

### Step 3: Scan Open Ports

Perform a TCP SYN scan to identify open ports on the target machine.

```bash
nmap -sS <target-ip>
```

### Step 4: Detect Services and Operating System

Identify running service versions and attempt to detect the target operating system.

```bash
nmap -sV -O <target-ip>
```

### Step 5: Save Nmap Results

Save the scan output in a text file for future analysis and documentation.

```bash
nmap -sV -oN nmap_scan_results.txt <target-ip>
```

### Step 6: Launch Nessus

Open the Nessus web interface in a browser.

```text
https://localhost:8834
```

Log in to Nessus and select **New Scan → Basic Network Scan**.

### Step 7: Configure and Launch the Scan

1. Enter a suitable scan name.
2. Provide the target machine's IP address.
3. Save the scan configuration.
4. Launch the vulnerability scan.
5. Wait for the scan to complete.

### Step 8: Review Vulnerabilities

Analyze the vulnerabilities detected by Nessus based on their severity levels:

| Severity | Description |
|---|---|
| Critical | Extremely serious security vulnerabilities |
| High | Vulnerabilities that may cause significant security risks |
| Medium | Security weaknesses requiring attention |
| Low | Minor security issues |
| Info | General information about the target system |

### Step 9: Document Findings

Record the important findings, especially Critical and High vulnerabilities.

The following details should be documented:

- CVE ID
- Vulnerability name
- Affected service and port
- Severity level
- Recommended remediation

## Expected Observations

- Identification of active hosts in the target network.
- Detection of open and closed ports.
- Identification of running services and their versions.
- Detection of possible operating system information.
- Identification of known vulnerabilities using Nessus.
- Recommendations for improving the security of the target machine.

## Result

The active hosts, open ports, running services, and known vulnerabilities of the target network were successfully identified and documented using Nmap and Nessus.

## Conclusion

This experiment demonstrated how Nmap and Nessus can be used together for network scanning and vulnerability assessment. Nmap helped identify network devices, open ports, and running services, while Nessus helped detect potential vulnerabilities and provided remediation recommendations.

## Ethical Considerations

- Perform scanning only on authorized systems and networks.
- Obtain permission before conducting vulnerability assessments.
- Avoid scanning public or third-party systems without authorization.
- Use the findings responsibly to improve network security.

