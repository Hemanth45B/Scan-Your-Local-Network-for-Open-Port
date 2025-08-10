# Scan-Your-Local-Network-for-Open-Port
 Learn to discover open ports on devices in your local network to understand  network exposure. 
## 🛠Tools Used
 Nmap:Used for network discovery and security auditing.
 Wireshark: Used for network protocol analysis and packet capture.

## Methodology

The analysis was conducted in two main phases:

1.  Network Scanning with Nmap:
    [cite_start]An initial Nmap SYN scan (`-sS`) was performed on the `192.168.1.0/24` subnet to identify live hosts and open ports[cite: 1, 19].
     [cite_start]The scan results were saved to a file (`scan_results.txt`) for later review[cite: 1].
    [cite_start]The scans identified several active hosts and their open ports, such as HTTP (80), HTTPS (443), and SSH (22) on `192.168.1.1` [cite: 3][cite_start], and Microsoft services on `192.168.1.2` and `192.168.1.5`[cite: 5, 52, 53, 54, 55, 56, 57, 58].

2.  Packet Analysis with Wireshark:
    [cite_start]Wireshark was used to capture network traffic during the Nmap scan to observe the discovery process at the packet level[cite: 70].
    [cite_start]A display filter (`tcp.flags.syn==1 and tcp.flags.ack==1`) was applied to isolate the SYN/ACK packets sent from live hosts in response to Nmap's SYN probes[cite: 71].
     [cite_start]This confirmed that hosts were responding to the scan attempts, validating the Nmap findings[cite: 71].

##  Key Findings

[cite_start]Active Hosts Identified: The scans successfully identified multiple live hosts on the network, including `192.168.1.1`, `192.168.1.2`, `192.168.1.5`, `192.168.1.7`, `192.168.1.8`, `192.168.1.13`, and `192.168.1.16`[cite: 2, 4, 6, 9, 11, 47, 60].
Open Services Discovered:
     [cite_start]192.168.1.1:*Running web services on ports 80 (HTTP) and 443 (HTTPS), DNS on port 53 (domain), and filtered ports for SSH (22) and Telnet (23) [cite: 3].
    [cite_start]192.168.1.2 & 192.168.1.5:** Running Windows services such as MSRPC (135), NetBIOS (139), and SMB (445)[cite: 5, 52, 54, 56].
    [cite_start]192.168.1.16: Had an open port for ICSLAP (2869)[cite: 12].

