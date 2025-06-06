# Bridged-Network-Kali-Ubuntu-Wireshark
Documentation for setting up a bridged network between Kali Linux and Ubuntu, testing connectivity, and analyzing traffic with Wireshark.

**Step 1**: Virtual Network Setup
A bridged network adapter was configured for both the Kali Linux and Ubuntu virtual machines. IP addresses were verified on both systems using the `ifconfig` command.
- Kali address obtained: 192.168.0.169  
- Ubuntu address obtained: 192.168.0.121

**Step 2**: Wireshark Installation
Wireshark was installed on the Ubuntu virtual machine using the following commands:
`sudo add-apt-repository ppa:wireshark-dev/stable`

![Image](https://github.com/user-attachments/assets/b13d535e-f1c0-4895-afe9-46543dab3530)

**Step 3:** Network Connectivity Test
Network connectivity between the two virtual machines was tested by pinging Kali Linux from Ubuntu and vice versa. The connection was successful.

![Image](https://github.com/user-attachments/assets/04903c00-4320-48c2-aa69-dbda7cf8089f)
From Ubuntu to Kali Linux:
`ping 192.168.0.169`  

![Image](https://github.com/user-attachments/assets/0b683c30-8042-4498-accf-50fa488a87ab)

From kali linux to ubuntu
`ping 192.168.0.121`

**Step 4:** Packet Capture and Filtering with Wireshark
Wireshark was opened on the Ubuntu virtual machine, and the active network interface (`enp0s3`) was selected for live packet capturing.
                                                                                                                                                                       
Network traffic was monitored in real time while performing actions such as browsing, pinging, and DNS lookups. The following packet types were captured and filtered for analysis:
![Image](https://github.com/user-attachments/assets/addbbb66-adcc-4b2e-a995-b7f140def3a2)
- TCP packets

![Image](https://github.com/user-attachments/assets/21e2697a-cdea-4446-88dc-f73f00ceb6c0)
- ICMP packets

 ![Image](https://github.com/user-attachments/assets/6237d1c9-936d-4893-942d-4511e63443c3)
- UDP packets

Filters Used in Wireshark:
Filters were applied using the filter bar at the top of the Wireshark interface:
- TCP filter:  `tcp`
- ICMP filter: `icmp`
- UDP filter:  `udp`

Each filter helped isolate specific types of traffic to better understand protocol behavior.

**Observations:**

-ICMP Packets: Captured during ping tests between Kali linux and Ubuntu. Wireshark displayed `echo request` and `echo reply` messages, confirming connectivity.

-TCP Packets: Seen during HTTP traffic generation (e.g., when visiting websites or using the `curl` command). The capture included `SYN`, `ACK`, and other TCP flags.

-UDP Packets: Detected from background services and DNS lookups. These packets included DNS query and response data.

**Step 5:** HTTP Traffic Analysis Using `curl`

To generate HTTP traffic, the `curl` command was executed on the Ubuntu virtual machine, with the command:

`curl -I http://altschoolafrica.com.`
![Image](https://github.com/user-attachments/assets/f5f02261-e209-4494-bf17-5a56b166d3c3)

While the command was running, Wireshark was actively capturing traffic on the network interface.
A http filter (http) was applied in Wireshark to isolate the packets related to the request.

The capture showed the "HTTP GET" request and the server's response headers.
This confirmed that HTTP communication was successfully established.


 **Achievements**
This exercise successfully achieved the following objectives:

- Configured a bridged network between Kali Linux and Ubuntu virtual machines.
- Verified network connectivity using `ping` tests.
- Installed and configured **Wireshark** on Ubuntu for packet capturing.
- Captured and filtered various types of network packets:
  - TCP
  - ICMP
  - UDP
  - HTTP (via the `curl` command)
- Analyzed captured traffic to observe:
  - ICMP echo requests and replies
  - TCP handshakes
- Applied Wireshark filters to isolate specific protocols during analysis.
- Demonstrated use of **network analysis tools** (Wireshark, curl) in a virtual environment.

**Skills Gained:**
- Basic networking concepts: IP addressing, bridging, ICMP, TCP/UDP
- Packet analysis using Wireshark
- HTTP request inspection using `curl`
- Troubleshooting network connectivity in virtualized systems
