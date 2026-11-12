# PC2 — Windows Security Monitoring Endpoint

## Overview

PC2 operates as a monitored Windows endpoint within my Cybersecurity SOC Home Lab.

The computer is integrated with the Wazuh SIEM/XDR platform to support endpoint visibility, security event collection, and practical SOC investigations.

The primary objective is to gain hands-on experience with Windows security monitoring and centralized log analysis.

## Hardware Configuration

- **Processor:** AMD Ryzen 5 5500
- **CPU Cores:** 6
- **CPU Threads:** 12
- **Memory:** 16 GB RAM
- **Storage:** SSD
- **Graphics:** Dedicated GPU with 8 GB VRAM
- **Network Connection:** Wi-Fi

## Operating System

- **Operating System:** Microsoft Windows 11 Home
- **Architecture:** 64-bit
- **Endpoint Security Platform:** Wazuh Agent
- **Agent Version:** 4.14

## Endpoint Security Configuration

### Wazuh Agent

The Wazuh Agent was installed and configured to communicate with the centralized Wazuh Manager.

The agent enables endpoint monitoring and security event collection from the Windows operating system.

### Monitored Event Sources

The laboratory includes monitoring of Windows event channels such as:

- Windows Security
- Windows System
- Windows Application

These event sources provide visibility into authentication activity, system operations, and application errors.

## Network Integration

PC2 connects to the laboratory network through Wi-Fi.

The endpoint communicates with the Wazuh Manager running on the virtualized SOC infrastructure.

Network connectivity was validated before agent deployment.

Internal IP addresses and sensitive network configurations are intentionally excluded.

## Security Monitoring Validation

The Wazuh Dashboard confirmed successful endpoint integration.

### Deployment Results

- **Wazuh Agent Installation:** Successful
- **Network Connectivity:** Verified
- **Agent Registration:** Completed
- **Manager Communication:** Established
- **Dashboard Agent Status:** Active
- **Endpoint Integration:** Successful

## Security Events Observed

### Windows Authentication Monitoring

The Wazuh platform successfully collected Windows authentication events.

Examples include:

- **Windows Event ID 4624:** Successful authentication
- **Wazuh Rule 60106:** Windows Logon Success
- **Logon Type 5:** Service authentication

These events were examined to understand Windows authentication mechanisms and distinguish expected system activity from potentially suspicious behavior.

### Application Monitoring

Application-related events were also observed.

An example included:

- **Windows Event ID 1022**
- **Event Source:** .NET Runtime
- **Event Category:** Application Error

This event was reviewed as part of a preliminary investigation into application behavior and runtime errors.

The available evidence did not establish a security compromise.

## Responsibilities

PC2 serves as:

- A monitored Windows endpoint.
- A source of Windows security events.
- A system for validating Wazuh Agent connectivity.
- An endpoint for practicing log analysis.
- A controlled environment for SOC monitoring exercises.

## Technical Skills Demonstrated

- Windows endpoint administration
- Wazuh Agent installation and configuration
- PowerShell
- Windows Event Viewer
- SIEM endpoint integration
- Windows authentication event analysis
- Security log investigation
- Endpoint monitoring and troubleshooting

---

**Project:** Cybersecurity SOC Home Lab

**Component:** Windows Monitoring Endpoint

**Status:** Operational
