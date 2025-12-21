---
title: "Network Forensics: TCP SYN Flood Analysis"
summary: "Analysed a packet capture with Wireshark and identified a TCP SYN flood denial-of-service attack targeting a web server; documented indicators and mitigation recommendations."
tags: [network-forensics, wireshark, tcp, syn-flood, dos]
layout: default
---

## Overview

This project analyses a packet capture to determine why a web server was unreachable. Using Wireshark, I identified traffic patterns consistent with a **TCP SYN flood (Denial of Service)** attack — a high-volume stream of TCP SYN packets directed at the web server without completing the TCP three-way handshake.

> ⚠️ **Disclaimer:** Packet captures and analysis notes are provided for educational and defensive purposes only. Do not use this material to perform unauthorised testing or attacks.

---

## Tools & Data

- **Primary tools:** Wireshark (GUI)  
- **Data:** Sanitised packet capture (`capture.pcap`) containing web server traffic  
- **Environment:** Local analysis workstation (isolated)

---

## What I did

- Loaded the packet capture in Wireshark and reviewed overall traffic statistics.  
- Analysed TCP flags to identify abnormal patterns, focusing on SYN, SYN-ACK, and ACK packets. 
- Analysed SYN packets.
- Correlated timestamps and source IP behaviour to confirm sustained flooding rather than legitimate traffic spikes.  
- Documented findings and proposed mitigations from a defensive perspective.

---

## Key findings

- **Attack classification:** TCP SYN flood (Distributed Denial of Service).  
- **Indicators observed:**  
  - Large spike in TCP SYN packets (`tcp.flags.syn == 1 && tcp.flags.ack == 0`) targeting the web server.  
  - Absence of ACK packets completing the three-way handshake.  
  - Numerous half-open connections accumulating on the server.  
  - High connection attempt rate from multiple source IP addresses (indicative of spoofing or a distributed attack).  
  - Repetitive packet characteristics suggesting automated attack tooling.
  - Targeting port 0 (not a valid port number for transport-layer communication).
  - SYN packets contain a non-zero acknowledgment number - indicating malformation.
- **Likely impact:**  
  - Exhaustion of the server’s connection table.  
  - Legitimate clients unable to establish connections, compromising availability.

---

## Mitigations & detection recommendations

- **Mitigations:**  
  - Enable **SYN cookies** on the web server or upstream devices to reduce the impact of half-open connections.  
  - Implement rate limiting or connection thresholds at firewalls and load balancers.  
  - Use intrusion prevention systems (IPS) or DDoS protection services to detect and block SYN floods.  

- **Detection & monitoring:**  
  - Monitor TCP flag distributions for abnormal SYN-to-ACK ratios.  
  - Alert on sudden spikes in new TCP connection attempts per second.  
  - Maintain baseline metrics for normal web traffic patterns to improve anomaly detection.

---

## Lessons learned

- Developed a deeper understanding of the TCP three-way handshake and how it can be exploited in denial-of-service attacks.  
- Learned how TCP flag analysis in Wireshark is critical for identifying SYN flood behaviour.  
- Confirmed that service unavailability can often be explained through traffic pattern analysis alone, even without server-side logs.  
- Practised documenting network forensic findings clearly for technical and non-technical stakeholders.

---
