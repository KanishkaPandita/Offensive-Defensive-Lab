# Experiment 5: Sniffing and Session Hijacking

## Overview

This experiment demonstrates how **ARP Spoofing, Man-in-the-Middle (MITM) attacks, and packet sniffing** can expose sensitive information transmitted over unencrypted HTTP connections.

The practical was performed in an isolated virtual lab using Kali Linux and Metasploitable 2 with DVWA. Wireshark was used to capture and analyze network traffic and understand the security risks associated with HTTP-based login sessions.

## Objective

To observe how ARP spoofing redirects network traffic through an intermediate machine and demonstrate how unencrypted HTTP communication can expose login information and session data.

## Lab Environment

| Component | Details |
|---|---|
| Analysis Machine | Kali Linux |
| Target Machine | Metasploitable 2 |
| Web Application | DVWA |
| Target IP | `192.168.1.100` |
| Gateway IP | `192.168.1.1` |
| Capture Interface | `eth0` |
| Packet Analyzer | Wireshark |

## Tools Used

- **Kali Linux:** Used for ARP spoofing and network analysis.
- **Metasploitable 2:** Vulnerable target machine.
- **DVWA:** Used for the HTTP login demonstration.
- **Wireshark:** Used to capture and analyze network packets.
- **ARP Spoofing Tool:** Used to demonstrate traffic redirection.

## Methodology

1. Verified connectivity between Kali Linux, the target machine, and the gateway.
2. Enabled IPv4 packet forwarding on Kali Linux.
3. Performed ARP spoofing between the target and gateway.
4. Verified traffic forwarding through Kali Linux.
5. Captured network traffic using Wireshark.
6. Generated a DVWA login request over HTTP.
7. Analyzed the captured HTTP POST request in Wireshark.
8. Verified the authenticated DVWA session through the browser.
9. Observed the security risks of unencrypted HTTP communication.

## Screenshots and Practical Implementation

### 1. Network Connectivity

Verified communication between Kali Linux, the target, and the gateway.

![Network Connectivity](screenshots/Screenshot%202026-10-15%20122202.png)

### 2. Enable IPv4 Forwarding

Enabled packet forwarding on Kali Linux to allow traffic to pass through the analysis machine.

![IPv4 Forwarding](screenshots/Screenshot%202026-10-15%20122611.png)

### 3. ARP Spoofing

ARP replies sent toward the target machine.

![ARP Spoofing Target](screenshots/Screenshot%202026-10-15%20122835.png)

ARP replies sent toward the gateway.

![ARP Spoofing Gateway](screenshots/Screenshot%202026-10-15%20122925.png)

### 4. Traffic Forwarding and Analysis

Confirmed that IPv4 forwarding was enabled.

![Forwarding Confirmation](screenshots/Screenshot%202026-10-15%20123051.png)

Captured and analyzed network traffic involving the target using Wireshark.

![Wireshark Traffic](screenshots/Screenshot%202026-10-15%20123249.png)

### 5. HTTP Traffic Capture

Generated a DVWA login request and checked the HTTP communication.

![HTTP Request](screenshots/Screenshot%202026-10-15%20123257.png)

Wireshark captured the DVWA login POST request over HTTP.

![HTTP POST Capture](screenshots/Screenshot%202026-10-15%20123526.png)

### 6. Authenticated DVWA Session

Verified the successful login through the DVWA browser interface.

![Authenticated Session](screenshots/Screenshot%202026-10-15%20124548.png)

## Observations

- Kali Linux successfully communicated with the target and gateway.
- ARP replies demonstrated traffic redirection between both machines.
- IPv4 forwarding allowed packets to pass through Kali Linux.
- Wireshark captured ICMP and HTTP traffic.
- A DVWA login POST request was observed over an unencrypted HTTP connection.
- The browser confirmed that the DVWA session was authenticated.
- The experiment demonstrated the risks of transmitting sensitive information without encryption.

## Result

The experiment successfully demonstrated ARP spoofing and Man-in-the-Middle traffic redirection in an isolated virtual network. Wireshark captured an unencrypted DVWA HTTP login request, showing how credentials and session information can be exposed to a network observer.

## Real-World Security Improvements

1. **Use HTTPS:** Encrypt communication between clients and servers using TLS.
2. **Enable Secure Cookies:** Use `Secure`, `HttpOnly`, and appropriate `SameSite` cookie attributes.
3. **Enable HSTS:** Force browsers to communicate with websites using HTTPS.
4. **Dynamic ARP Inspection:** Prevent unauthorized ARP responses on supported managed switches.
5. **Network Segmentation:** Separate sensitive systems from untrusted devices.
6. **Monitor ARP Traffic:** Detect unusual changes in IP-to-MAC address mappings.
7. **Session Management:** Regenerate session IDs after login and expire inactive sessions.

## Learning Outcomes

- Understood the concept of ARP spoofing.
- Learned how Man-in-the-Middle attacks work.
- Practiced network packet capturing using Wireshark.
- Observed the risks of unencrypted HTTP communication.
- Understood the importance of HTTPS and secure session management.

## Evidence and Security Note

The `screenshots/` directory contains nine screenshots used in this documentation.

Four additional screenshots containing plaintext login fields or session cookie values have intentionally been excluded to protect sensitive information. Original evidence should be kept private or properly redacted before sharing.

## Reproduction Note

The screenshots represent one virtual lab run. IP addresses and interface names may differ in other environments. Use disposable lab accounts and isolated virtual machines.

## Disclaimer

This experiment was conducted strictly for educational purposes in an authorized and isolated virtual lab.

Do not perform ARP spoofing, packet interception, or session hijacking on public networks or devices without explicit permission.

---

**Experiment:** 5 – Sniffing and Session Hijacking  
**Domain:** Network Security and Ethical Hacking  
**Environment:** Kali Linux + Metasploitable 2 + DVWA
