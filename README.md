# day-1
Objective: Learn to discover open ports on devices in your local network to  understand network exposure.  Tools: Nmap (free), Wireshark (optional)

1. Installed npmap from "https://nmap.org/download#windows" official website.
2. open command prompt by searching in windows search or use WIN+R and type cmd
3. use command "ipconfig"
4. it gives me my ip4 address from which i can choose range.
   --> 192.168.188.1 to 192.168.188.254
5.  run Nmap as administrator. type  the command
   --> nmap -sS 192.168.188.0/24
6. Nmap go es through all ip addressess in the given range and checks which devices are online. It identifies open port on each and tries to detect what service is running. The scan took 2-3 minutes.
7. Here i got 2 host "192.168.188.53" and "192.168.188.174" Now we have active IPs, Open ports and its services.

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

8.
