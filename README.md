# AWS VPC Peering Assessment Report

## Overview
This repository contains the submission-ready technical documentation and proof-of-concept evidence for the **AWS VPC Peering Assessment**. The project demonstrates inter-VPC private connectivity between two isolated Virtual Private Clouds (`ewb-vpc-a` and `ewb-vpc-b`) in the **ap-southeast-2 (Sydney)** region using native AWS VPC Peering, explicit subnet route tables, and SSH Bastion ProxyJump access.

---

## Architecture Summary
- **VPC A (`ewb-vpc-a`)**: `10.10.0.0/16`
  - Public Subnet: `ewb-rt-a-public` (Holds Bastion host `13.211.203.157`)
  - Private Subnet: `ewb-rt-a-private` (Holds App-A `10.10.2.10`)
- **VPC B (`ewb-vpc-b`)**: `10.20.0.0/16`
  - Private Subnet: `ewb-rt-b-private` (Holds App-B `10.20.1.10`)
- **Peering Connection**: `ewb-a-b-peer` (`pcx-022336ab0aac38f2e`) [Active]

---

## Verified Evidence & Key Deliverables

All 9 mandatory assessment checkpoints and connectivity tests were verified with 100% compliance:

1. **Checkpoint 01 — Subnet Route Table Associations**: Confirmed explicit associations for public/private route tables.
2. **Checkpoint 02 — EC2 Instances**: Validated running statuses for `ewb-bastion`, `ewb-app-a`, and `ewb-app-b`.
3. **Checkpoint 03 — Active VPC Peering**: Verified `pcx-022336ab0aac38f2e` status as `Active` across non-overlapping CIDRs.
4. **Checkpoint 04 — Updated Route Tables**: Confirmed cross-VPC routes (`10.20.0.0/16` and `10.10.0.0/16`) pointing to target `pcx-022336ab0aac38f2e`.
5. **Test 01 — App-A to App-B Ping**: Bidirectional ICMP echo succeeded (0% packet loss, avg RTT 0.324 ms).
6. **Test 02 — App-B to App-A Ping**: ICMP echo succeeded (0% packet loss, avg RTT 0.282 ms).
7. **Test 03 — SSH ProxyJump Connection**: Successfully established secure SSH terminal connection to private `ewb-app-b` via `ewb-bastion`.
8. **Test 04 — Controlled ICMP Failure**: Simulated traffic isolation resulting in 100% packet loss.
9. **Test 05 — ICMP Recovery**: Restored security rules and routing, achieving full recovery (0% packet loss, avg RTT 0.028 ms).

---

## File Structure
- `YourName_EWB_VPC_Peering.pdf` — Full submission report containing architecture diagrams, configuration metrics, terminal logs, and console screenshot evidence.

- 
