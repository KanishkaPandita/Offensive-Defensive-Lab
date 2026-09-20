Experiment: Simulated Ethical Hacking with Metasploit

Objective

To perform a safe exploitation of a vulnerable virtual machine using Metasploit and understand the basic ethical hacking procedure.

Procedure

Step 1: Start the Virtual Machines
Start the Kali Linux and Metasploitable virtual machines and ensure they are connected to the same virtual network.

Step 2: Identify the Target IP Address
Determine the IP address of the Metasploitable machine using:

ifconfig

Step 3: Scan the Target
Use Nmap from Kali Linux to identify open ports and available services:

nmap -sV 192.168.42.136

Step 4: Launch Metasploit Framework
Open the Metasploit console in Kali Linux:

msfconsole

Step 5: Search for a Suitable Exploit
Search the Metasploit database for an exploit corresponding to a vulnerable service on the target:

search <service/vulnerability>

Step 6: Select and Configure the Exploit
Select the required exploit and configure the target IP address:

use <exploit>
set RHOSTS 192.168.42.136

Set the required options and verify the configuration.

Step 7: Execute the Exploit
Run the exploit against the authorized Metasploitable virtual machine:

exploit

Step 8: Verify the Result
Observe the Metasploit output and verify whether a session was successfully established.

Step 9: Close the Session
After completing the demonstration, terminate the session and exit Metasploit.

Result

The exploitation of the vulnerable virtual machine was performed safely using Metasploit, demonstrating the basic ethical hacking and vulnerability exploitation process.
