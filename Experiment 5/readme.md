# Experiment 5: Sniffing and Session Hijacking

## Overview

This experiment demonstrates how **ARP Spoofing, Man-in-the-Middle (MITM) attacks, and packet sniffing** can expose sensitive information transmitted over unencrypted HTTP connections.

The experiment was performed in an isolated virtual lab using Kali Linux and Metasploitable 2 with DVWA. Wireshark was used to capture and analyze network traffic and observe the security risks associated with HTTP-based login sessions.

## Objective

To understand how ARP spoofing can redirect network traffic through an intermediate machine and demonstrate how unencrypted HTTP communication can expose login information and session data.

## Lab Environment

| Component | Details |
|---|---|
| Attacker / Analysis Machine | Kali Linux |
| Target Machine | Metasploitable 2 |
| Web Application | DVWA |
| Target IP | `192.168.1.100` |
| Gateway IP | `192.168.1.1` |
| Network Interface | `eth0` |
| Packet Analyzer | Wireshark |

## Tools Used

- **Kali Linux:** Used to perform network analysis and ARP spoofing.
- **Metasploitable 2:** Vulnerable target machine.
- **DVWA:** Web application used for the login demonstration.
- **Wireshark:** Used to capture and analyze HTTP packets.
- **ARP Spoofing Tool:** Used to demonstrate traffic redirection in the isolated lab.

## Methodology

1. Verified connectivity between Kali Linux, the target machine, and the gateway.
2. Enabled IPv4 packet forwarding on Kali Linux.
3. Performed ARP spoofing between the target and gateway.
4. Verified that network traffic was passing through Kali Linux.
5. Captured network packets using Wireshark.
6. Generated a DVWA login request over HTTP from the target environment.
7. Analyzed the captured HTTP POST request and observed the authenticated DVWA session.
8. Studied the security risks of transmitting sensitive information without encryption.

## Observations

- Both the target machine and gateway were reachable from Kali Linux.
- ARP replies demonstrated traffic redirection between the target and gateway.
- IPv4 forwarding allowed packets to continue through Kali Linux.
- Wireshark captured ICMP and HTTP traffic.
- A DVWA login POST request was observed over an unencrypted HTTP connection.
- The browser confirmed that the DVWA session was authenticated.

## Screenshots / Evidence

The following screenshots document the practical implementation.

### 1. Network Connectivity

Verified connectivity between Kali Linux, the target, and the gateway.

![Network Connectivity](screenshots/Screenshot%202026-10-15%20122202.png)

### 2. IPv4 Forwarding

Enabled packet forwarding on Kali Linux.

![IPv4 Forwarding](screenshots/Screenshot%202026-10-15%20122611.png)

### 3. ARP Spoofing

ARP replies sent toward the target machine.

![ARP Spoofing Target](screenshots/Screenshot%202026-10-15%20122835.png)

ARP replies sent toward the gateway.

![ARP Spoofing Gateway](screenshots/Screenshot%202026-10-15%20122925.png)

### 4. Traffic Forwarding and Analysis

Confirmed IPv4 forwarding and inspected network packets.

![Forwarding Confirmation](screenshots/Screenshot%202026-10-15%20123051.png)

Wireshark captured traffic involving the target machine.

![Wireshark Traffic](screenshots/Screenshot%202026-10-15%20123249.png)

### 5. HTTP Traffic Capture

Generated a DVWA login request and analyzed the HTTP traffic.

![HTTP Request](screenshots/Screenshot%202026-10-15%20123257.png)

Wireshark displayed the DVWA login POST request over HTTP.

![HTTP POST Capture](screenshots/Screenshot%202026-10-15%20123526.png)

### 6. Authenticated DVWA Session

Verified successful login through the DVWA browser interface.

![Authenticated DVWA Session](screenshots/Screenshot%202026-10-15%20124548.png)

## Result

The experiment successfully demonstrated ARP spoofing and Man-in-the-Middle traffic redirection in an isolated virtual network. Wireshark captured an unencrypted DVWA HTTP login request, showing how sensitive information and session data can be exposed when secure communication is not used.

## Security Recommendations

1. **Use HTTPS:** Encrypt communication between clients and web servers using TLS.
2. **Enable Secure Cookies:** Set the `Secure`, `HttpOnly`, and appropriate `SameSite` cookie attributes.
3. **Use HSTS:** Enforce HTTPS connections through HTTP Strict Transport Security.
4. **Enable Dynamic ARP Inspection:** Help prevent unauthorized ARP responses on managed switches.
5. **Use Network Segmentation:** Separate critical systems from untrusted devices.
6. **Monitor ARP Traffic:** Detect unusual changes in IP-to-MAC address mappings.

## Learning Outcomes

- Understood the working of ARP spoofing.
- Learned the concept of Man-in-the-Middle attacks.
- Practiced packet capturing and analysis using Wireshark.
- Observed the risks of unencrypted HTTP communication.
- Understood the importance of HTTPS and secure session management.

## Disclaimer

This experiment was conducted strictly for educational purposes in an isolated virtual lab using authorized machines.

Do not perform ARP spoofing, packet interception, or session hijacking on public networks or devices without explicit permission.

Sensitive screenshots containing plaintext credentials or session cookie values have been excluded from this repository. Original evidence should be stored privately or properly redacted before sharing.

---

**Experiment:** 5 – Sniffing and Session Hijacking  
**Environment:** Kali Linux + Metasploitable 2 + DVWA  
**Category:** Network Security / Ethical Hacking
