# 🏢 Enterprise SOHO Network Design & Implementation  
### Cisco Packet Tracer

<img src="https://github.com/z30r0x/Authentication_App/blob/5a832f90aee859d94685c0f024476a5b3fa57b18/images/welcome.jpg" width="200" height="400" style="margin: 10px;">

## 📌 Project Overview

This project demonstrates the design and implementation of a Small Office/Home Office (SOHO) Enterprise Network using Cisco Packet Tracer 2022.
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


## ⚙️ Switch Configuration

enable
configure terminal

vlan 10
name ADMIN_IT

vlan 20
name FINANCE_HR

vlan 30
name CUSTOMER_SERVICE

interface range fa0/2-4
switchport mode access
switchport access vlan 10

interface range fa0/5-7
switchport mode access
switchport access vlan 20

interface range fa0/8-10
switchport mode access
switchport access vlan 30

interface fa0/1
switchport mode trunk

end
write memory

## 🌐 Router Configuration (Router-on-a-Stick)

enable
configure terminal

interface g0/0
no shutdown

interface g0/0.10
encapsulation dot1Q 10
ip address 192.168.1.1 255.255.255.192

interface g0/0.20
encapsulation dot1Q 20
ip address 192.168.1.65 255.255.255.192

interface g0/0.30
encapsulation dot1Q 30
ip address 192.168.1.129 255.255.255.192

## 📡 DHCP Configuration

ip dhcp excluded-address 192.168.1.1
ip dhcp excluded-address 192.168.1.65
ip dhcp excluded-address 192.168.1.129

ip dhcp pool ADMIN
network 192.168.1.0 255.255.255.192
default-router 192.168.1.1
dns-server 8.8.8.8

ip dhcp pool FINANCE
network 192.168.1.64 255.255.255.192
default-router 192.168.1.65
dns-server 8.8.8.8

ip dhcp pool CUSTOMER
network 192.168.1.128 255.255.255.192
default-router 192.168.1.129
dns-server 8.8.8.8

end
write memory
