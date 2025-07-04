# day-1
This project demonstrate how to scan a local network and to discover open ports on acive devices in your local network to understand network exposure and potential security risks.  Tools: Nmap (free), Wireshark (optional)

Steps:
1. Installed npmap from "https://nmap.org/download#windows" official website.
2. open command prompt by searching in windows search or use WIN+R and type cmd
3. use command "ipconfig"
4. it gives me my ip4 address from which i can choose range.
   --> 192.168.188.1 to 192.168.188.254
5.  run Nmap as administrator. Run the TCP SYN SCAN command to identify open ports
   --> nmap -sS 192.168.188.0/24
6. Nmap goes through all ip addressess in the given range and checks which devices are online. It identifies open port on each and tries to detect what service is running. The scan took 2-3 minutes.
7. Here, I got 2 host "192.168.188.53" and "192.168.188.174". Now we have active IPs, Open ports and its services.

output:
Starting Nmap 7.97 ( https://nmap.org ) at 2025-06-23 21:43 +0530
Nmap scan report for 192.168.188.53
Host is up (0.026s latency).
Not shown: 999 closed tcp ports (reset)
PORT   STATE SERVICE
53/tcp open  domain
MAC Address: DE:E7:3B:B9:8B:7D (Unknown)

Nmap scan report for 192.168.188.174
Host is up (0.0017s latency).
Not shown: 993 closed tcp ports (reset)
PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
902/tcp  open  iss-realsecure
912/tcp  open  apex-mesh
2869/tcp open  icslap
5357/tcp open  wsdapi

Nmap done: 256 IP addresses (2 hosts up) scanned in 135.61 seconds

8. Analyzing Packet capture with wireshark
   8.1 Install wire shark from the official website "https://www.wireshark.org/download.html"
   8.2 Open wireshark and start capturing on correct interface ( i have choosesn only wireless )
   8.3 Run Nmap scan while wireshark is capturing
   8.4 Stop the capture once the scan is finished
   8.5 can save the capture as a documentation. ( File-> SavesAs)
   8.6 Can also apply filters to inspect packets ( exp: dns, tcp.port == 135...)
9.  Common services on ports
    53   -- DNS
    135  -- Windows RPC
    139  -- NetBIOS over TCP/IP
    902  -- VMware-related port
    912  -- Custom /local app
    5357  -- Windows services for device discovery

10. Security Risks
    135,139,445 -- High Risk level --> can be a block on public networks
    602,5357 -- Medium Risk level
    53 -- low Risj=k level 
    
11.To save Nmap TCP SYN scan file as txt
   --> nmap -sS 192.168.188.0/24 -oN scan_results.txt  or   -->  nmap -sS 192.168.188.0/24 -oN "C:\Users\ARULMOZHI\Documents\nmap_scan.txt"



 Outcome: Basic network reconnaissance ski ls; understanding network service
 exposure.
