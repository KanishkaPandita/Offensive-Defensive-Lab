Experiment 1: Scanning for Vulnerabilities in a Network

Objective
To identify active hosts and open ports on a target network using Nmap, and to detect known vulnerabilities on those hosts using Nessus. 

Procedure
Step 1: Identify the IP address of the Kali machine
Open the terminal in the Kali Linux machine and execute:
ifconfig
The IP address of the Kali machine is identified as 192.168.42.136.

Step 2: Identify the IP address of the target machine
Open the terminal in the Metasploitable machine and identify its IP address. The IP address of the Metasploitable machine is 192.168.159.136.
Then, from Kali:
ping 192.168.42.136
After confirming connectivity, Nmap is used from Kali Linux to scan Metasploitable (192.168.42.136).

Step 3: Verify connectivity between the Kali and target machines
From the Kali terminal, send ICMP packets to the target machine using:
ping 192.168.42.136
The successful replies confirm that the Kali machine can communicate with the target.

Step 4: Scan the target machine for open ports
Use Nmap to scan the target machine:
nmap -Pn -n 192.168.42.136

The scan identifies the open TCP ports and their associated services. The output shows ports such as 21 (FTP), 22 (SSH), 23 (Telnet), 25 (SMTP), 80 (HTTP), 139 (NetBIOS-SSN), 445 (Microsoft-DS), 3306 (MySQL), 5432 (PostgreSQL), 5900 (VNC), 6000 (X11) and others as open.

Step 5: Launch Nessus
Open the Nessus web interface in a browser, typically:
https://localhost:8834
Launch Nessus and proceed to the Nessus interface.

Step 6: Configure and run the Nessus scan
Create a new Basic Network Scan and enter the target IP address:
192.168.42.136
Save and launch the scan. Nessus analyzes the target for known security vulnerabilities.

Step 7: Review the Nessus vulnerability results
After the scan is completed, open the scan results. Nessus displays the vulnerabilities according to their severity, such as Critical, High, Medium, Low and Informational.

The obtained results include findings such as UnrealIRCd Backdoor Detection, VNC Server Password Password, SSL Version 2 and 3 Protocol Detection, Bind Shell Backdoor Detection, Apache Tomcat Multiple Issues, SSL Multiple Issues, NFS Shares World Readable, and Samba Backdoor Vulnerability.
