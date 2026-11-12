# PC1 — SOC Infrastructure Host

## Overview

PC1 serves as the primary infrastructure host for my Cybersecurity SOC Home Lab.

This computer provides the virtualization environment required to deploy and manage security monitoring solutions, including the Wazuh SIEM/XDR platform.

The objective is to simulate a small-scale Security Operations Center (SOC) environment for hands-on cybersecurity training.

## Hardware Configuration

- **Processor:** AMD Ryzen 5 5500
- **CPU Cores:** 6
- **CPU Threads:** 12
- **Memory:** 16 GB RAM
- **Storage:** NVMe SSD
- **Graphics:** Dedicated GPU with 12 GB VRAM
- **Network Connection:** Ethernet

## Host Operating System

- **Operating System:** Windows 11 Home
- **Virtualization Platform:** Oracle VirtualBox
- **Network Environment:** Private Home Lab

## Virtualization Environment

Oracle VirtualBox is used to deploy Linux-based virtual machines and security monitoring infrastructure.

### Wazuh Server Virtual Machine

- **Guest Operating System:** Ubuntu Server 24.04 LTS
- **Security Platform:** Wazuh 4.14
- **Deployment Model:** All-in-One
- **Virtual CPU:** 4 vCPUs
- **Allocated Memory:** 8 GB RAM
- **Virtual Disk:** Approximately 60 GB
- **Network Mode:** NAT

### Installed Security Components

- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard
- Filebeat

These components provide centralized security monitoring, log analysis, alert management, and endpoint visibility.

## Network Architecture

The virtualization host communicates with other laboratory endpoints through a local network.

VirtualBox NAT networking is used to provide network connectivity to the virtualized Wazuh Server.

Controlled port forwarding enables communication between the Wazuh Manager and monitored endpoints.

Specific network addresses and forwarding rules are intentionally excluded from public documentation.

## Responsibilities

PC1 performs the following functions:

- Hosts the virtualized Wazuh Server.
- Provides centralized security monitoring infrastructure.
- Processes and stores security events.
- Hosts the Wazuh Dashboard.
- Supports security analysis and investigation exercises.
- Provides the foundation for SOC laboratory activities.

## Deployment Validation

- **Virtualization Environment:** Operational
- **Ubuntu Server Installation:** Successful
- **Wazuh Platform Installation:** Successful
- **Wazuh Dashboard Access:** Verified
- **Endpoint Communication:** Established
- **Security Monitoring Infrastructure:** Operational

## Technical Skills Demonstrated

- Virtual machine deployment
- Windows and Linux administration
- VirtualBox configuration
- SIEM/XDR infrastructure implementation
- Network configuration and troubleshooting
- Security monitoring architecture

---

**Project:** Cybersecurity SOC Home Lab

**Component:** SOC Infrastructure Host

**Status:** Operational
