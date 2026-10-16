# Experiment 5: Observing an HTTP Session

## Aim
To observe and analyze HTTP traffic using Wireshark and understand the security risks of unencrypted communication.

## Objectives
- Understand how HTTP communication works.
- Observe ARP spoofing in an isolated virtual lab.
- Capture network packets using Wireshark.
- Identify HTTP POST requests and understand the importance of HTTPS.

## Tools and Technologies
- Kali Linux
- Metasploitable 2
- DVWA (Damn Vulnerable Web Application)
- Wireshark
- VMware Workstation

## Lab Configuration

| Component | Details |
|---|---|
| Packet analyzer | Kali Linux |
| Target machine | Metasploitable 2 |
| Web application | DVWA |
| Target IP | `192.168.1.100` |
| Gateway IP | `192.168.1.1` |
| Network interface | `eth0` |

## Procedure

1. Verified connectivity between Kali Linux, the target machine, and the gateway.
2. Enabled IP forwarding on Kali Linux.
3. Observed ARP spoofing in both directions within the isolated lab.
4. Captured network traffic using Wireshark.
5. Inspected the HTTP traffic and identified the `POST /dvwa/login.php` request.
6. Verified that the DVWA page was displayed after successful test authentication.

## Results
The experiment demonstrated that HTTP traffic can be observed by an intermediary when network traffic is redirected through a controlled lab system. Wireshark captured an HTTP POST request, illustrating the risks of transmitting sensitive information without encryption.

## Security Recommendations
- Use HTTPS with valid TLS certificates.
- Protect session cookies using appropriate security attributes.
- Monitor suspicious ARP activity.
- Avoid sending sensitive information over unencrypted HTTP.

## Screenshots
The `screenshots/` folder contains sanitized evidence of network connectivity, IP forwarding, ARP observations, Wireshark captures, and the DVWA test session.

## Learning Outcomes
- Learned basic HTTP traffic analysis using Wireshark.
- Understood ARP spoofing and IP forwarding concepts.
- Identified the security limitations of unencrypted HTTP.
- Learned why HTTPS and TLS are important for data protection.

## Ethical Notice
This experiment was performed for educational purposes in an isolated virtual lab. Traffic interception and ARP spoofing must only be performed on systems and networks for which explicit authorization has been granted.

**Note:** Never upload passwords, authentication tokens, or reusable session cookies to GitHub.
