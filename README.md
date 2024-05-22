# Network Home Lab

This repository contains the configuration and documentation for a network home lab setup. The lab is designed to simulate a small enterprise network with various departments and services. The documentation covers the hardware components, network topology, VLAN configurations, and other essential network settings.

## Hardware Components

- Router: 1 x Cisco 2911 (R1)
- Multilayer Switches: 2 x Cisco 3560-24PS
- Layer 2 Switches: 5 x Cisco 2960-24TT
- Servers:
  - 1 x Web Server
  - 1 x DHCP Server
  - 1 x DNS Server
- Access Point: 1 x Wireless Access Point

## Network Topology
![network_topology](https://github.com/iamabdullahifti/network_home_lab/assets/129957445/829003e4-736c-4f85-b108-722aac90074a)

The network is divided into five segments:

- IT Department: VLAN 10 - 192.168.10.0/24
- HR Department: VLAN 20 - 192.168.20.0/24
- Sales Department: VLAN 30 - 192.168.30.0/24
- Internal Segment: VLAN 40 - 192.168.40.0/24 (includes DNS server, Web server, and management)
- Wireless Segment: 192.168.50.0/24 (no VLAN)
  
## Logical Topology
![logical_topology](https://github.com/iamabdullahifti/network_home_lab/assets/129957445/4c117701-47dd-4fda-a764-4466b26eb9c4)

## VLAN Assignments and IP Ranges

- IT Department: VLAN 10 - 192.168.10.0/24
- HR Department: VLAN 20 - 192.168.20.0/24
- Sales Department: VLAN 30 - 192.168.30.0/24
- Internal Segment: VLAN 40 - 192.168.40.0/24
- Wireless Segment: 192.168.50.0/24 (no VLAN)

## Multilayer Switch SVI Configuration

- Multilayer SW 1 SVI:
  - VLAN 10: 192.168.10.1
  - VLAN 20: 192.168.20.1
  - VLAN 30: 192.168.30.1
  - VLAN 40: 192.168.40.1

- Multilayer SW 2 SVI:
  - VLAN 10: 192.168.10.2
  - VLAN 20: 192.168.20.2
  - VLAN 30: 192.168.30.2
  - VLAN 40: 192.168.40.2

## VLAN Gateways

- VLAN 10: 192.168.10.100
- VLAN 20: 192.168.20.100
- VLAN 30: 192.168.30.100
- VLAN 40: 192.168.40.100


## HSRP Configuration

- HSRP Standby:
  - DSW1 Active: VLAN 10
  - DSW2 Active: VLAN 20, VLAN 30, VLAN 40

## Network Connections

- Each department VLAN (IT, HR, Sales, Management) connects to a layer 2 switch.
- These layer 2 switches connect to the two multilayer switches (SW1 and SW2).
- The multilayer switches then connect to the router (R1).
- The wireless segment connects to an access point (AP).
- Both the AP and the DHCP server connect to a switch which then connects to the router.
- The wireless segment is kept separate from the other networks and uses the 192.168.50.0/24 subnet.

## Default Static Routes and OSPF Configuration

- Default Static Route: Default route is configured to R1 on MSW1 and MSW2.
- OSPF Configuration:
  - OSPF was configured on MSW1 and MSW2 on the network IDs of the VLANs and on G0/1 interface, which connects to the router.
  - OSPF was configured on all the interfaces on R1.

## DNS and Web Server Configuration

- DNS Server: Configured on the internal VLAN (192.168.40.0/24).
- Web Server: Configured on the internal VLAN (192.168.40.0/24).

## Wireless Network Configuration

- DHCP Server: Configured to provide IP addresses for the wireless segment (192.168.50.0/24).
- Access Point (AP): Connected to a switch which then connects to the router.
- Wireless clients connect to the AP and obtain IP addresses via DHCP.

## Usage

This lab setup can be used to simulate a small enterprise network environment. It is useful for learning and testing purposes related to network configuration, VLAN management, routing protocols, and network services such as DNS and DHCP.

## Contributions

Contributions are welcome! Please submit pull requests for any improvements or changes.

## License

This project is licensed under the MIT License.
