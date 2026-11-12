# Wazuh SIEM/XDR — Deployment and Configuration

## Project Overview

This project documents the installation, configuration, and troubleshooting of Wazuh SIEM/XDR in a virtualized Security Operations Center (SOC) home laboratory.

The environment was designed to provide hands-on experience with security monitoring infrastructure, centralized log management, Linux administration, and troubleshooting security platforms.

The deployment follows an All-in-One architecture, integrating the Wazuh Indexer, Wazuh Manager, and Wazuh Dashboard into a single virtual server.

## Lab Environment

### Virtualization
- **Hypervisor:** Oracle VirtualBox
- **Deployment Type:** Local Virtualized Laboratory
- **Deployment Model:** All-in-One
- **Architecture:** x86-64

### Operating Systems
- **Host Operating System:** Windows 11
- **Guest Operating System:** Ubuntu Server 24.04 LTS

### Security Platform
- **SIEM/XDR Solution:** Wazuh 4.14

### Network Configuration
- **Network Mode:** VirtualBox NAT
- **Management Interface:** HTTPS

Specific network addresses, administrative credentials, and sensitive configuration details are intentionally excluded from this public documentation.

## Wazuh Architecture

The environment consists of three integrated Wazuh components.

### Wazuh Indexer

Responsible for storing, indexing, and searching security-related information.

It provides the data storage and search capabilities required for security event analysis.

### Wazuh Manager

Responsible for processing security events, managing monitoring agents, evaluating security rules, and generating alerts.

### Wazuh Dashboard

Provides a centralized web interface for security monitoring, visualization, investigation, and platform administration.

### Architecture Diagram

```text
        Security Event Sources
                  |
                  v
           Wazuh Manager
                  |
                  v
           Wazuh Indexer
                  |
                  v
           Wazuh Dashboard
                  |
                  v
           SOC Monitoring
```

The components communicate within the virtualized laboratory environment.

## Deployment Procedure

### 1. Operating System Preparation

Ubuntu Server 24.04 LTS was selected as the operating system for the Wazuh deployment.

The operating system was updated, and the required installation utilities were prepared.

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install curl -y
```

### 2. Wazuh Installation

The official Wazuh installation assistant was used to deploy the platform.

```bash
curl -fLO https://packages.wazuh.com/4.14/wazuh-install.sh
```

The All-in-One installation was initiated using:

```bash
sudo bash ./wazuh-install.sh -a
```

This installation method deploys the core Wazuh components on a single server.

### 3. Service Verification

After installation, the status of the main services was verified using systemd.

```bash
sudo systemctl is-active wazuh-indexer
sudo systemctl is-active wazuh-manager
sudo systemctl is-active wazuh-dashboard
```

**Result:** All three services were confirmed active.

### 4. Dashboard Verification

The Wazuh Dashboard was accessed through an HTTPS connection from the host environment.

The configuration uses VirtualBox NAT networking with controlled port forwarding.

The web interface was successfully accessed after troubleshooting service initialization and authentication issues.

**Result:** Wazuh Dashboard access confirmed.

## Troubleshooting and Technical Challenges

The deployment involved several technical issues that required investigation and corrective actions.

### Issue 1 — Operating System Compatibility

**Problem**

An initial deployment was attempted using a newer Ubuntu Server release, resulting in compatibility warnings.

**Investigation**

The installed operating system version was verified using:

```bash
cat /etc/os-release
```

**Resolution**

The environment was reinstalled using Ubuntu Server 24.04 LTS.

**Technical Learning**

Operating system compatibility must be verified before deploying security monitoring platforms.

### Issue 2 — Virtual Machine Resource Allocation

**Problem**

The initial virtual machine configuration had insufficient memory allocated for the complete Wazuh deployment.

**Investigation**

System resources were evaluated using:

```bash
free -h
df -h /
nproc
```

**Resolution**

Virtual machine memory allocation was adjusted to better support the Wazuh components.

**Technical Learning**

Resource planning is essential when multiple security services operate within the same virtual machine.

### Issue 3 — Dashboard Installation Delay

**Problem**

The Wazuh Dashboard installation took significantly longer than expected.

**Investigation**

System processes and package installation logs were analyzed.

```bash
ps -eo pid,stat,etime,%cpu,%mem,cmd
```

```bash
sudo tail -n 30 /var/log/dpkg.log
```

**Finding**

The package manager was still processing the Dashboard installation.

**Resolution**

Installation progress was monitored until package configuration completed.

**Technical Learning**

Long-running installation processes should be investigated before being interrupted.

### Issue 4 — Dashboard Initialization

**Problem**

The web interface initially displayed:

```text
Wazuh dashboard server is not ready yet
```

**Investigation**

Service status, network listeners, and system logs were examined.

```bash
sudo systemctl status wazuh-indexer
sudo systemctl status wazuh-dashboard
```

```bash
sudo journalctl -u wazuh-indexer --no-pager
sudo journalctl -u wazuh-dashboard --no-pager
```

**Finding**

The investigation identified temporary communication errors between the Dashboard and Indexer during service initialization.

**Resolution**

Service availability, HTTPS connectivity, and authentication were verified. Dashboard access was subsequently confirmed.

**Technical Learning**

An active service does not necessarily indicate that its application dependencies are fully operational.

### Issue 5 — Indexer Authentication

**Problem**

An initial authenticated request to the Wazuh Indexer returned an authorization error.

**Investigation**

The Indexer's HTTPS response was tested without exposing credentials in command arguments.

```bash
curl -k -I https://127.0.0.1:9200
```

**Finding**

The Indexer returned an HTTP authentication challenge, confirming that the service was responding over HTTPS.

**Resolution**

The correct administrative credentials were identified from the installation's protected credential archive, and authenticated access was confirmed.

**Technical Learning**

Secure credential management and authentication verification are important parts of maintaining SIEM infrastructure.

## Security Considerations

The laboratory was configured with attention to secure administration and controlled access.

Security practices include:

- Restricting management access to the local laboratory environment.
- Using HTTPS for administrative connections.
- Avoiding the publication of credentials, authentication tokens, and private keys.
- Excluding sensitive installation archives from version control.
- Separating public technical documentation from private configuration data.
- Reviewing screenshots and terminal outputs before publication.

**Security Notice:** This repository does not contain passwords, private keys, authentication tokens, or sensitive configuration archives.

## Deployment Validation

| Validation | Result |
|---|---|
| Ubuntu Server installation | Completed |
| Wazuh Indexer deployment | Completed |
| Wazuh Manager deployment | Completed |
| Wazuh Dashboard deployment | Completed |
| Main service verification | Successful |
| HTTPS connectivity | Verified |
| Indexer authentication | Verified |
| Dashboard access | Successful |
| Installation troubleshooting | Documented |

## Technical Skills Demonstrated

**Security Operations**

- SIEM/XDR infrastructure deployment
- Security monitoring architecture
- Centralized security event management
- Wazuh platform administration

**Systems Administration**

- Linux server configuration
- Virtual machine deployment
- System resource monitoring
- Service management with systemd
- Linux package management

**Networking and Troubleshooting**

- VirtualBox NAT configuration
- HTTPS connectivity testing
- Network service verification
- System log investigation
- Application dependency troubleshooting
- Authentication diagnostics

**Documentation**

- Technical implementation documentation
- Troubleshooting procedures
- Infrastructure validation
- Security-conscious documentation practices

---

**Project:** Cybersecurity SOC Home Lab  
**Component:** Wazuh SIEM/XDR  
**Author:** Mikael Rodrigues Pereira  
**Environment:** Isolated Virtualized Laboratory  
**Purpose:** Hands-on Cybersecurity Training and Professional Portfolio
