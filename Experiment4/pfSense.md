# Experiment 4: Firewall and IDS Setup Using pfSense and Snort

##  Aim
To build a virtual network, configure **pfSense as a firewall**, install **Snort as an Intrusion Detection System (IDS)**, and analyze network traffic generated from Kali Linux using Nmap.

##  Objectives
- Configure pfSense as a network firewall.
- Create an isolated virtual network using VMware.
- Install and configure Snort IDS.
- Enable GPLv2 Community Rules.
- Generate network scanning traffic using Nmap.
- Monitor and analyze IDS alerts.

##  Lab Requirements
- VMware Workstation or VMware Player
- pfSense Firewall VM
- Kali Linux VM
- Metasploitable VM
- VMware NAT Network (VMnet8)
- VMware Private Network (VMnet1)
- Snort package for pfSense
- GPLv2 Community Rules

##  Network Topology

```text
                    Internet
                       |
                VMware NAT (VMnet8)
                       |
                   pfSense WAN
                  [ Firewall ]
                   pfSense LAN
                  192.168.1.1
                       |
                Private LAN (VMnet1)
                   /          \
                  /            \
          Kali Linux        Metasploitable
        192.168.1.101       192.168.1.100
          Nmap Scanner       Test Target
```

##  IP Address Configuration

| Device | IP Address | Network | Purpose |
|---|---|---|---|
| pfSense WAN | DHCP | VMnet8 | Upstream connectivity |
| pfSense LAN | 192.168.1.1/24 | VMnet1 | Firewall and gateway |
| Kali Linux | 192.168.1.101/24 | VMnet1 | Traffic generation |
| Metasploitable | 192.168.1.100/24 | VMnet1 | Test target |

##  Procedure

### 1. Configure the Virtual Network
- Create three virtual machines in VMware.
- Connect pfSense WAN to VMnet8.
- Connect pfSense LAN, Kali Linux, and Metasploitable to VMnet1.
- Keep the test machines on the isolated lab network.

### 2. Configure pfSense LAN
- Assign WAN and LAN interfaces.
- Set the LAN IP address to `192.168.1.1/24`.
- Configure Kali Linux as `192.168.1.101/24`.
- Configure Metasploitable as `192.168.1.100/24`.
- Set the gateway to `192.168.1.1` where required.

Test connectivity from Kali Linux:

```bash
ping -c 4 192.168.1.1
ping -c 4 192.168.1.100
```

### 3. Configure Firewall Rules
Navigate to **Firewall → Rules → LAN** in the pfSense WebGUI.

- Configure only the required traffic rules.
- Allow required services such as DNS, HTTP, and HTTPS when needed.
- Review rule order and existing rules before applying changes.
- Use a final block rule only after confirming that necessary management and lab traffic will not be interrupted.

### 4. Install Snort
- Open **System → Package Manager → Available Packages**.
- Search for Snort and install it.
- Navigate to **Services → Snort** to verify that the package is available.

### 5. Configure Snort IDS
- Open **Services → Snort → Snort Interfaces**.
- Add the LAN interface (em1) for monitoring.
- Save and apply the configuration.
- Verify that the interface and Snort service are enabled.

### 6. Enable Community Rules
- Open Snort's global settings or rules update settings.
- Enable the GPLv2 Community Rules source.
- Update the rules.
- Enable relevant downloaded rules and apply the configuration.

### 7. Generate Test Traffic Using Nmap
From Kali Linux, scan the authorized Metasploitable target:

```bash
nmap -sV 192.168.1.100
```

The `-sV` option attempts to identify running services and their versions.

### 8. Analyze IDS Alerts
- Open **Services → Snort → Alerts** in pfSense.
- Review alerts generated during the scan.
- Compare alert timestamps with the Nmap scan time.
- If no alerts appear, check the Snort service, monitored interface, enabled rules, and traffic visibility.

**Note:** A packet capture confirms that traffic was observed, but it does not by itself prove that Snort generated an alert.

## 📊 Results and Observations
The experiment workflow covers the configuration of pfSense, installation of Snort, activation of community rules, and generation of Nmap traffic from Kali Linux toward Metasploitable.

The setup demonstrates how a firewall manages network traffic and how an IDS can inspect monitored traffic for patterns matching security rules.

Record the actual Snort alerts, rule IDs, detected services, and screenshots after running the experiment. No specific alert count or detection result is assumed in this README.

##  Conclusion
This experiment provides practical experience with firewall configuration and intrusion detection in a virtual network. It demonstrates how pfSense and Snort can be used together to monitor network activity and investigate possible scanning behavior.

##  Security Notes
- Run scans only against systems you own or have permission to test.
- Keep Metasploitable isolated from public networks.
- Do not expose the vulnerable target to the internet.
- Back up pfSense configuration before changing firewall rules.

##  Tools and Technologies
- **pfSense:** Firewall and network security
- **Snort:** Intrusion Detection System (IDS)
- **Kali Linux:** Security testing platform
- **Nmap:** Network scanning and service detection
- **Metasploitable:** Intentionally vulnerable test machine
- **VMware:** Virtualization platform

##  Learning Outcomes
- Understanding firewall rules and network segmentation.
- Learning IDS installation and rule configuration.
- Generating and analyzing network scanning traffic.
- Understanding the difference between packet capture and IDS alerts.
- Practicing security monitoring in an isolated lab environment.
