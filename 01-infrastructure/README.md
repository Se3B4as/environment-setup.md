# 🖥️ Home Lab Infrastructure

## 1. Overview

This section documents the physical infrastructure of my Cybersecurity Home Lab.

The environment consists of two desktop computers connected to the same local network. Both machines will be used to build a practical environment for cybersecurity studies, infrastructure administration, network analysis, security monitoring, and incident response.

The infrastructure was designed to provide a flexible environment for hands-on experiments and technical learning.

## 2. Hardware Infrastructure

### PC 1 – Main Machine

- **Processor:** AMD Ryzen 5 5500
- **Memory:** 16 GB RAM
- **Storage:** NVMe SSD
- **Operating System:** Windows 11 Home
- **Network Connection:** Ethernet

### PC 2 – Secondary Machine

- **Processor:** AMD Ryzen 5 5500
- **Memory:** 16 GB RAM
- **Storage:** SATA SSD
- **Operating System:** Windows 11 Home
- **Network Connection:** Wi-Fi

## 3. Network Infrastructure

Both computers are connected to the same router and operate within the same local network.

**Network Configuration:**

- PC 1: Wired Ethernet connection
- PC 2: Wireless Wi-Fi connection
- Shared router
- Local network communication

## 4. Infrastructure Architecture

The initial infrastructure consists of two physical machines connected through a shared network.

```text
             INTERNET
                 |
              ROUTER
                 |
          LOCAL NETWORK
             /     \
            /       \
         PC 1       PC 2
       Ethernet     Wi-Fi
          |           |
       Windows 11  Windows 11
       16 GB RAM   16 GB RAM
       NVMe SSD    SATA SSD
```

## 5. Lab Objectives

The infrastructure will be used to:

- Practice Windows administration and security.
- Understand network communication between machines.
- Explore network security concepts.
- Perform security monitoring and log analysis.
- Study threat detection and incident response.
- Develop practical SOC and Blue Team skills.

## 6. Future Infrastructure Improvements

As the lab evolves, the following components may be introduced:

- Virtualization environments.
- Windows Server.
- Active Directory.
- SIEM solutions.
- Network monitoring tools.
- Centralized log collection.
- Security testing environments.


**Author:** Mikael Rodrigues Pereira

**Project:** Cybersecurity Home Lab

**Category:** Infrastructure & Cybersecurity
