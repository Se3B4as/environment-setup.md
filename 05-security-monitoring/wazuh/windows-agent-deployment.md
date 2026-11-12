# Wazuh Agent Deployment — Windows 11

## Project Overview

This document describes the installation, configuration, and successful integration of a Windows 11 endpoint into a virtualized Wazuh SIEM/XDR environment.

The objective was to establish communication between a Windows endpoint and the Wazuh Manager, enabling centralized security monitoring and endpoint visibility.

The implementation was completed in a controlled Cybersecurity SOC Home Lab.

## Lab Environment

### Endpoint
- **Operating System:** Microsoft Windows 11
- **Security Agent:** Wazuh Agent 4.14
- **Connection Type:** Local Network
- **Deployment Status:** Successfully Connected

### Server Infrastructure
- **SIEM/XDR Platform:** Wazuh 4.14
- **Server Operating System:** Ubuntu Server 24.04 LTS
- **Hypervisor:** Oracle VirtualBox
- **Deployment Model:** All-in-One
- **Virtual Network:** NAT
- **Communication Protocol:** TCP

Internal addresses, hostnames, agent identifiers, credentials, and sensitive configuration details are intentionally excluded.

## Deployment Architecture

The deployment consists of a Windows endpoint communicating with a Wazuh Manager hosted in a virtualized Linux environment.

```text
+--------------------------+
| Windows 11 Endpoint      |
| Wazuh Agent              |
+--------------------------+
             |
             | Local Network
             v
+--------------------------+
| Virtualization Host      |
| VirtualBox NAT           |
| Controlled Port Forward  |
+--------------------------+
             |
             v
+--------------------------+
| Ubuntu Server            |
| Wazuh Manager            |
| Wazuh Indexer            |
| Wazuh Dashboard          |
+--------------------------+
```

## Deployment Procedure

### 1. Network Preparation

The Wazuh Manager was deployed inside a virtual machine using NAT networking.

Port forwarding was configured to allow communication between the Windows endpoint and the virtualized security monitoring infrastructure.

Connectivity was verified using Windows PowerShell before agent installation.

### 2. Connectivity Validation

PowerShell's `Test-NetConnection` utility was used to verify connectivity to the required Wazuh services.

```powershell
Test-NetConnection <MANAGER_ADDRESS> -Port <AGENT_COMMUNICATION_PORT>
```

The same procedure was performed for the agent enrollment service.

**Result:** Both connectivity tests completed successfully.

### 3. Wazuh Agent Installation

The official Wazuh Agent installation package was downloaded from the Wazuh software repository.

The Windows Installer utility (`msiexec.exe`) was used to perform a silent installation.

Installation parameters included:

- Wazuh Manager address
- Agent enrollment server
- Agent identification
- Silent installation options

Specific environment values have been omitted from this public documentation.

### 4. Windows Service Verification

The Wazuh Agent service was verified using PowerShell.

```powershell
Get-Service -Name WazuhSvc
```

The service was configured to communicate with the Wazuh Manager.

### 5. Agent Registration

Following installation, the Windows endpoint successfully registered with the Wazuh Manager.

The Wazuh Dashboard confirmed that the endpoint was connected and reporting an active status.

**Result: Agent registration successful.**

## Troubleshooting

### Issue 1 — PowerShell Argument Parsing

**Problem**

The initial installation command failed because PowerShell could not correctly interpret the Windows Installer arguments.

**Investigation**

The installation package was verified using:

```powershell
Test-Path "<INSTALLER_PATH>"
```

The verification confirmed that the installation package was available.

**Resolution**

The installation command was simplified by invoking the Windows Installer executable directly.

**Technical Learning**

PowerShell quotation rules and argument parsing are important when automating Windows software installations.

### Issue 2 — Virtual Network Communication

**Challenge**

The endpoint needed to communicate with a security monitoring server hosted inside a NAT-based virtual machine.

**Investigation**

TCP connectivity tests were performed to verify that the required Wazuh services were reachable.

**Resolution**

VirtualBox port forwarding was configured, and successful connectivity was confirmed before proceeding with agent installation.

**Technical Learning**

Network connectivity should be validated before troubleshooting application-level communication.

## Security Considerations

The environment follows security-conscious documentation practices.

- Administrative credentials are excluded from public documentation.
- Internal IP addresses and hostnames are not disclosed.
- Agent identifiers are omitted.
- Sensitive configuration files are not included.
- Management access is restricted to the laboratory environment.
- Screenshots must be reviewed and sanitized before publication.
- Authentication tokens and private keys are not stored in the repository.

## Deployment Validation

- **Windows Agent Installation:** Successful
- **Network Connectivity:** Verified
- **Agent Enrollment:** Completed
- **Wazuh Manager Communication:** Established
- **Dashboard Agent Status:** Active
- **Endpoint Integration:** Successful

## Technical Skills Demonstrated

### Endpoint Security
- Windows endpoint integration
- Wazuh Agent deployment
- Endpoint monitoring infrastructure
- Agent enrollment and registration

### Networking
- TCP connectivity validation
- VirtualBox NAT networking
- Port forwarding configuration
- Client-server communication troubleshooting

### Windows Administration
- PowerShell
- Windows Installer (MSI)
- Windows service management
- Installation troubleshooting

### Security Operations
- SIEM/XDR endpoint integration
- Centralized endpoint monitoring
- Security infrastructure validation
- Technical troubleshooting

---

**Project:** Cybersecurity SOC Home Lab

**Component:** Windows Endpoint Integration with Wazuh

**Deployment Status:** Successfully Completed
