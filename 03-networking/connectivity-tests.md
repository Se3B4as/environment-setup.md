# Network Connectivity Tests — Wazuh SOC Home Lab

## Overview

This document describes the network connectivity tests performed during the integration of a Windows 11 endpoint with the Wazuh SIEM/XDR infrastructure.

The objective was to verify that the Windows endpoint could communicate with the virtualized Wazuh Manager before deploying the security agent.

All tests were conducted within a controlled local laboratory environment.

## Testing Environment

### Source System

- **Operating System:** Windows 11
- **Connection Type:** Wi-Fi
- **Role:** Monitored Endpoint
- **Testing Tool:** Windows PowerShell

### Destination System

- **Operating System:** Ubuntu Server 24.04 LTS
- **Security Platform:** Wazuh 4.14
- **Virtualization:** Oracle VirtualBox
- **Network Mode:** NAT
- **Role:** SIEM/XDR Server

## Test 01 — Agent Communication

### Objective

Verify that the Windows endpoint could reach the Wazuh Manager communication service.

### Command

Executed in Windows PowerShell:

```powershell
Test-NetConnection <MANAGER_ADDRESS> -Port 1514
```

### Result

```text
TcpTestSucceeded : True
```

**Status: PASSED**

The result confirmed that the agent communication port was reachable.

## Test 02 — Agent Enrollment

### Objective

Verify connectivity to the Wazuh Agent enrollment service.

### Command

```powershell
Test-NetConnection <MANAGER_ADDRESS> -Port 1515
```

### Result

```text
TcpTestSucceeded : True
```

**Status: PASSED**

The result confirmed that the enrollment service was reachable.

## Test 03 — Wazuh Manager Services

### Objective

Verify that the Wazuh Manager was listening on the required network ports.

### Command

Executed on the Ubuntu Server:

```bash
sudo ss -lntp | grep -E ':1514|:1515'
```

### Observations

The server reported listening services associated with:

- Wazuh agent communication
- Wazuh agent enrollment

**Status: PASSED**

## Test 04 — Agent Registration

### Objective

Confirm that the Windows endpoint could successfully register with the Wazuh Manager.

### Validation Method

The Wazuh Dashboard was used to verify the agent registration status.

### Results

- Agent successfully installed.
- Agent registration completed.
- Agent communication established.
- Endpoint appeared in the Wazuh Dashboard.
- Agent status reported as Active.

**Status: PASSED**

## Troubleshooting

### Issue — NAT Network Communication

**Problem**

The Wazuh Server was hosted inside a VirtualBox NAT-based virtual machine.

The Windows endpoint required access to the Wazuh Manager services running inside the virtualized environment.

### Investigation

The required communication ports were identified and tested.

The network configuration was reviewed to determine whether incoming connections could reach the virtual machine.

### Resolution

VirtualBox port forwarding was configured for the required Wazuh services.

Connectivity was then validated using PowerShell.

### Lessons Learned

- NAT networking requires additional configuration for inbound connections.
- TCP connectivity should be validated before installing dependent applications.
- PowerShell provides useful tools for network troubleshooting.
- Service availability can be verified directly on Linux using `ss`.
- Successful TCP connectivity does not independently guarantee successful application authentication.

## Validation Summary

- **TCP 1514 Connectivity:** Successful
- **TCP 1515 Connectivity:** Successful
- **Wazuh Manager Listening Services:** Verified
- **Agent Enrollment:** Successful
- **Agent Connection:** Active
- **Overall Result:** PASSED

## Technical Skills Demonstrated

- Network connectivity testing
- Windows PowerShell
- Linux networking commands
- TCP port validation
- VirtualBox NAT troubleshooting
- SIEM endpoint communication
- Technical troubleshooting documentation

---

**Project:** Cybersecurity SOC Home Lab

**Component:** Network Connectivity Validation

**Status:** Successfully Completed
