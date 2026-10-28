# TCP Port Scan Detection and Incident Response Using Wireshark

## 1. Project Overview
I performed a controlled network security test on my Kali Linux machine using Nmap and Wireshark. The goal was to identify TCP port scanning activity, inspect the packets, apply a temporary firewall rule, and verify the result.

## 2. Tools Used
- Kali Linux
- Nmap
- Wireshark
- iptables firewall

## 3. Initial Investigation
I started a local test web server on port 8080 and scanned ports 22, 80, 443, and 8080 using Nmap.

Wireshark captured TCP SYN packets sent to these ports.

## 4. Findings
- Ports 22, 80, and 443 responded with RST, ACK packets, indicating that they were closed.
- Port 8080 responded with SYN, ACK, indicating that a service was listening.
- The rapid SYN requests were consistent with a TCP SYN port scan.

This was a controlled lab test. The scan alone does not prove malicious activity.

## 5. Response
I added a temporary iptables rule to drop traffic to port 8080 through the local loopback interface.

## 6. Verification
After adding the rule, Nmap reported port 8080 as filtered with no response. The firewall rule's packet counter increased, confirming that packets matched the rule.

I captured the test traffic in Wireshark.

## 7. Cleanup
I removed the temporary firewall rule and stopped the local test web server after completing the test.

## 8. Conclusion
This project helped me practise packet analysis, TCP port scan detection, firewall rule testing, and verification of a security response.
