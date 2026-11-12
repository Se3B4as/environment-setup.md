# Network Configuration — Cybersecurity SOC Home Lab

## Overview

This document describes the network configuration implemented in my Cybersecurity SOC Home Lab.

The environment consists of two physical computers connected to the same local network, with a virtualized Wazuh SIEM/XDR server and a monitored Windows endpoint.

The objective is to establish reliable communication between the endpoint and the security monitoring infrastructure.

## Network Infrastructure

### Physical Network

- **Number of Physical Computers:** 2
- **Primary Host Connection:** Ethernet
- **Monitored Endpoint Connection:** Wi-Fi
- **Network Type:** Private Local Area Network (LAN)
- **Virtualization Platform:** Oracle VirtualBox

Both physical computers communicate through the same local network.

## Virtual Network Configuration

### VirtualBox Networking

The Wazuh Server operates inside an Ubuntu Server virtual machine using VirtualBox NAT networking.

NAT allows the virtual machine to access external networks through the virtualization host.

To enable inbound communication from the monitored Windows endpoint, controlled port forwarding was configured.

### Network Architecture

```text
+----------------------------+
| Windows 11 Endpoint        |
| Wazuh Agent                |
| Wi-Fi Connection           |
+----------------------------+
              |
              | Local Network
              v
+----------------------------+
| Physical Network           |
| Local Router               |
+----------------------------+
              |
              | Ethernet
              v
+----------------------------+
| Windows 11 Host            |
| Oracle VirtualBox          |
| NAT Port Forwarding        |
+----------------------------+
              |
              v
+----------------------------+
| Ubuntu Server VM           |
| Wazuh Manager              |
| Wazuh Indexer              |
| Wazuh Dashboard            |
+----------------------------+
```

## Wazuh Network Communication

The following services are used for endpoint communication:

- **TCP 1514:** Wazuh Agent communication
- **TCP 1515:** Wazuh Agent enrollment

VirtualBox port forwarding directs incoming connections from the physical network to the Wazuh Manager inside the virtual machine.

The management dashboard is accessed through HTTPS.

## Security Considerations

- Internal IP addresses are excluded from public documentation.
- Administrative credentials are not stored in the repository.
- Network forwarding is limited to services required by the laboratory.
- Management interfaces should remain restricted to trusted networks.
- Sensitive network configurations are not published.
- The laboratory is intended for controlled cybersecurity training.

## Configuration Validation

- **Local Network Connectivity:** Verified
- **Virtual Machine Network Access:** Operational
- **NAT Port Forwarding:** Configured
- **Wazuh Agent Communication:** Established
- **Agent Enrollment:** Successful
- **Endpoint Monitoring:** Active

## Technical Skills Demonstrated

- LAN configuration
- VirtualBox NAT networking
- TCP/IP networking
- Port forwarding
- Client-server communication
- Network troubleshooting
- SIEM infrastructure connectivity

---

**Project:** Cybersecurity SOC Home Lab

**Component:** Network Configuration

**Status:** Operational
