# Experiment 3: Basic Network Traffic Analysis with Wireshark

---

## Objective

To capture and examine network packets using Wireshark to identify suspicious activity and cleartext credentials within a simulated network environment.

---

## Procedure

---

### Step 1: Configure VM Network

Set the network adapters of Kali Linux and Metasploitable to Host-Only / Internal Network.

Kali Linux:
`ip a`

Metasploitable:
`ifconfig`

---

### Step 2: Install Required Packages

Run the following command on Kali Linux:

`sudo apt update && sudo apt install nmap wireshark tcpdump tshark -y`

Launch Wireshark:

`sudo wireshark`

---

### Step 3: Verify Connectivity

Test connectivity from Kali Linux to the target machine:

`ping -c 3 192.168.56.101`

---

### Step 4: Port and Service Scanning

Perform a SYN scan to identify open ports and services:

`sudo nmap -sS -Pn 192.168.56.101`

---

### Step 5: Start Wireshark Packet Capture

Open Wireshark and select the network interface connected to the Host-Only network.

Click the blue shark fin icon to start packet capture before generating network traffic.

---

### Step 6: Generate Lab Traffic

Generate unencrypted traffic while Wireshark is capturing.

HTTP:

`curl http://192.168.56.101/`

FTP:

`ftp 192.168.56.101`

Username: `msfadmin`  
Password: `msfadmin`

Telnet:

`telnet 192.168.56.101`

Username: `msfadmin`  
Password: `msfadmin`

---

### Step 7: Filter and Analyze Traffic

Target IP filter:

`ip.addr == 192.168.56.101`

FTP credential filter:

`ftp.request.command == "USER" || ftp.request.command == "PASS"`

Telnet filter:

`telnet`

Right-click a packet → Follow → TCP Stream

HTTP filter:

`http`

HTTP authentication filter:

`http.authorization`

---

### Step 8: Save Capture and Export Evidence

Stop the packet capture.

Select File → Save As and save the capture as:

`lab_capture.pcap`

To export HTTP objects:

File → Export Objects → HTTP

---

## Result

Network traffic was successfully captured and analyzed using Wireshark. HTTP, FTP, and Telnet traffic were examined to demonstrate how unencrypted protocols can expose sensitive information such as usernames and passwords.
