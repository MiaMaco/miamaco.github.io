---
title: "Network Forensics: ICMP Flood Analysis"
summary: "Analysed a packet capture with Wireshark and identified an ICMP flooding (DoS) attack; documented indicators and mitigation recommendations."
tags: [network-forensics, wireshark, icmp, dos]
layout: default
---

## Overview

This project analyses a packet capture to determine whether a network attack occurred. Using Wireshark, I identified traffic patterns consistent with an **ICMP flood (DoS)** — a high‑rate stream of ICMP echo requests directed at one targeted server.

> ⚠️ **Disclaimer:** Packet captures and analysis notes are provided for educational and defensive purposes. Do not use this material to perform unauthorised testing or attacks.

---

## Tools & Data

- **Primary tools:** Wireshark (GUI)  
- **Data:** Sanitised packet capture (`capture.pcap`) used for analysis  
- **Environment:** Local analysis workstation (isolated)

---

## What I did

- Inspected the capture to determine protocol distribution and temporal traffic patterns.  
- Isolated ICMP traffic and measured volume, packet rates, and source distributions.  
- Identified a concentrated set of source IPs generating a disproportionately large number of ICMP echo requests.  
- Analysed timestamps and packet characteristics to confirm sustained flooding behavior rather than normal or sporadic ICMP activity.  
- Compiled findings and recommended mitigations for network defenders.

---

## Key findings

- **Attack classification:** ICMP flood (Denial of Service) — sustained high volume of ICMP echo requests.  
- **Indicators observed:**  
  - Significant spike in ICMP packets within a short time window (high packets/sec).  
  - Majority of ICMP packets were echo requests (`icmp.type == 8`) with few corresponding replies.  
  - A small group of source IPs accounted for most of the traffic (top talkers).  
  - Packet payloads and sizes were repetitive, consistent with automated flooding tools.  
- **Likely impact:** Increased load on target host/network and potential service disruption or degraded performance.

---

## Mitigations & detection recommendations

- **Mitigations:**  
  - Implement ICMP rate limiting at network edges and on hosts as appropriate.  
  - Leverage upstream filtering or blackholing when traffic saturates bandwidth.  
  - Apply access control lists (ACLs) to block or restrict unnecessary ICMP traffic.

- **Detection & monitoring:**  
  - Configure alerts for sudden spikes in ICMP traffic or packets-per-second beyond normal baselines.  
  - Maintain traffic baselines to improve anomaly detection.  
  - Correlate flow data and host logs to assess impact and scope.

---

## Lessons learned

- Gained a deeper understanding of the Internet Control Message Protocol (ICMP), its role in network diagnostics (e.g. ping, traceroute), how it operates at Layer 3, and how it can be misused in denial-of-service scenarios.
- Volume and pattern analysis are often sufficient to identify ICMP flooding events. 
- Preparing sanitised artifacts and concise findings helps communicate incidents to network operators and stakeholders.

---

## Repository

[🔗 GitHub Repo](https://github.com/miamaco/network-forensics-icmp-flood)
