# 🏢 Enterprise SOHO Network Design & Implementation  

<img src="Screenshot 2026-03-01 014852.png" width="400" height="300" style="margin: 20px;">

## 📌 Project Overview

This project demonstrates the design and implementation of a Small Office/Home Office (SOHO) Enterprise Network using Cisco Packet Tracer.
The network was built based on real enterprise requirements including VLAN segmentation, Inter-VLAN routing, DHCP configuration, and wireless integration.

## 🏗 Scenario

XYZ Company is opening a new branch that must operate independently from the headquarters network.

### Requirements:

- One Cisco Router  
- One Cisco Switch  
- Three Departments:
  - Admin / IT
  - Finance / HR
  - Customer Service / Reception
- Each department must:
  - Be placed in a separate VLAN
  - Have wireless connectivity
- All devices must:
  - Obtain IPv4 addresses automatically (DHCP)
  - Communicate with other departments

Base network provided by ISP:
192.168.1.0/24

## 🛠 Technologies Used

- VLANs
- Inter-VLAN Routing (Router-on-a-Stick)
- DHCP Server Configuration
- Wireless Access Points
- 802.1Q Trunking
- Subnetting
- Network Segmentation

## 📊 VLAN & IP Addressing Plan

| Department | VLAN ID | Network | Default Gateway |
|------------|----------|----------|-----------------|
| Admin/IT | 10 | 192.168.1.0/26 | 192.168.1.1 |
| Finance/HR | 20 | 192.168.1.64/26 | 192.168.1.65 |
| Customer Service | 30 | 192.168.1.128/26 | 192.168.1.129 |

