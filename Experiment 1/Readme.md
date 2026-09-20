Experiment Name: Basic Network Traffic Analysis with Wireshark  

Objective: Capture and examine network packets to detect suspicious activity and cleartext credentials within a simulated network environment.  

Procedure

Set VM network adapters to Host-Only / Internal mode.
Identify VM IP addresses (ip a on Kali; ifconfig on Metasploitable).
Ensure required packages are installed:
sudo apt update && sudo apt install nmap wireshark tcpdump tshark -y

Launch Wireshark with capture privileges:
sudo wireshark

Execution Steps -
Step 1: Verify Connectivity Test connectivity from the Kali VM to the target machine:
ping -c 3 192.168.42.136

Step 2: Port & Service Scanning Perform a SYN scan to detect open ports and running services:
sudo nmap -sS -Pn 192.168.42.136

Step 3: Start Wireshark Packet Capture (Missing Step)
In the Wireshark interface, select the active network interface corresponding to the Host-Only network (e.g., eth0 or eth1).
Click the blue shark fin icon (Start Capture) to begin live packet capture before generating traffic.

Step 4: Generate Lab Traffic Execute network interactions to generate unencrypted traffic while capture is active:
HTTP:
curl http://192.168.42.136/
FTP:
ftp 192.168.56.101
# Login: msfadmin / Password: msfadmin
Telnet:
telnet 192.168.56.101
# Login: msfadmin / Password: msfadmin

Step 5: Filter & Analyze Plaintext Credentials Apply display filters in Wireshark to locate cleartext data:
Filter target IP traffic: ip.addr == 192.168.56.101
Inspect FTP credentials: ftp.request.command == "USER" || ftp.request.command == "PASS"
Inspect Telnet session traffic: telnet (Right-click packet → Follow → TCP Stream)
Inspect HTTP traffic & authentication: http or http.authorization

Step 6: Save Capture & Export Evidence
Stop packet capture.
Save session: File → Save As → lab_capture.pcap.
Export transferred objects: File → Export Objects → HTTP.
