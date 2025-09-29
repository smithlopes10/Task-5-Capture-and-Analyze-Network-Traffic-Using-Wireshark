# Task-5-Capture-and-Analyze-Network-Traffic-Using-Wireshark
Internship at Elevate Labs

## Objective
Capture live network packets and identify basic protocols and traffic types using Wireshark.

## Tools
- Wireshark (installed on Kali Linux VM)

## Steps Performed

1. Opened Wireshark on Kali Linux.
2. Selected the active network interface (`eth0` or `wlan0`) and started packet capture.
3. Generated traffic by:
   - Pinging a server: `ping -c 4 google.com`
4. Stopped capture after approximately 1 minute.
5. Applied protocol filters:
   - `dns` for Domain Name System traffic
   - `icmp` for ping packets
   - `arp` for Address Resolution Protocol
   - `ntp` for Network Time Protocol
6. Exported the capture as a `.pcap` file:
   - Original: `TASK5.pcap`
   - Sanitized: `TASK5.txt` (private IPs rewritten)

---

## Protocols Identified

| Protocol | Description | Example Packets |
|----------|-------------|----------------|
| DNS      | Resolves domain names to IP addresses | `192.168.*.* → 192.168.*.* DNS query A google.com` |
| ICMP     | Ping requests and replies | `192.168.*.* → 142.251.42.238 ICMP Echo Request` |
| ARP      | Resolves local IP to MAC addresses | `Broadcast: Who has 192.168.*.*? Tell 192.168.234.1` |
| NTP      | Time synchronization with external server | `192.168.*.* → 160.191.28.140 NTP request` |

> **Note:** Only private/local IPs (`192.168.*.*`) were sanitized for safe upload. Public IPs (Google, NTP) remain unchanged.

---

## Observations

- ARP packets were broadcasted to determine the MAC address of the local gateway.
- DNS queries resolved both IPv4 (A) and IPv6 (AAAA) addresses for websites.
- ICMP packets verified connectivity to remote servers using ping.
- NTP packets synchronized system time with external servers.
- Using filters in Wireshark allowed isolating each protocol for analysis.

---


