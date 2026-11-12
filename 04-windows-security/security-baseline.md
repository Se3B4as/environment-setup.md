# Windows 11 Security Baseline Assessment

## Overview

This document describes an initial Windows 11 security baseline assessment performed in a personal Cybersecurity SOC Home Lab.

The assessment uses Wazuh Security Configuration Assessment (SCA) to identify configuration weaknesses and evaluate the endpoint against predefined security recommendations.

The objective is to gain practical experience with endpoint security assessment, configuration auditing, and security monitoring.

## Lab Environment

- **Operating System:** Microsoft Windows 11
- **Security Platform:** Wazuh 4.14
- **Monitoring Component:** Wazuh Agent
- **Assessment Framework:** CIS Microsoft Windows 11 Benchmark
- **Deployment Type:** Controlled Home Lab

Sensitive infrastructure information has been intentionally excluded.

## Security Configuration Assessment

Wazuh SCA evaluates system configurations against security policies and predefined checks.

These checks help identify potential security weaknesses, configuration inconsistencies, and opportunities for improving endpoint security.

### Assessment Areas

The benchmark includes checks related to:

- Operating system security settings
- Windows Update configuration
- User account security
- Authentication policies
- Administrative privileges
- System hardening
- Security-related configuration controls

## Observed Security Events

During the initial Wazuh Threat Hunting analysis, several SCA-related alerts were identified.

### Wazuh Rule 19005

**Description:** SCA summary — CIS Microsoft Windows 11 Enterprise Benchmark v3.0.0: Score less than 30%.

- **Rule ID:** 19005
- **Rule Level:** 9
- **Category:** Security Configuration Assessment
- **Observation:** The assessment reported a score below 30%.

This finding indicates that the evaluated system did not satisfy many of the checks included in the applied benchmark.

However, the result requires further review because the benchmark edition and individual checks may not fully match the endpoint's operating system edition or intended laboratory configuration.

A low compliance score does not independently confirm a security compromise.

### Additional Configuration Findings

Other observed alerts included:

- **Rule 19007:** Configuration assessment findings
- **Rule 19008:** Configuration assessment findings
- **Rule 19009:** Configuration assessment findings

The observed checks included Windows Update and feature update settings.

These findings provide opportunities to study endpoint hardening and security configuration management.

## Preliminary Assessment

The initial assessment successfully demonstrated that Wazuh can identify and report security configuration findings on the Windows endpoint.

### Validated Results

- **Wazuh SCA Monitoring:** Operational
- **Security Benchmark Evaluation:** Observed
- **Configuration Findings:** Detected
- **Security Alerts:** Generated
- **Endpoint Visibility:** Established

### Limitations

- Individual findings have not all been manually validated.
- No remediation results have been confirmed.
- Benchmark applicability requires review.
- The overall compliance score should not be interpreted as a complete measure of endpoint security.

## Security Operations Relevance

Security Configuration Assessment is useful for:

- Identifying insecure configurations
- Supporting endpoint hardening
- Evaluating security controls
- Prioritizing remediation
- Monitoring compliance-related findings
- Improving security visibility

## Technical Skills Demonstrated

- Windows security configuration assessment
- Wazuh SCA
- CIS Benchmark interpretation
- Security alert analysis
- Endpoint security auditing
- Configuration risk identification

---

**Project:** Cybersecurity SOC Home Lab

**Component:** Windows Security Baseline Assessment

**Status:** Initial Assessment Completed
