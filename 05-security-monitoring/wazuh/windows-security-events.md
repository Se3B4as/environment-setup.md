# Windows Security Event Monitoring with Wazuh

## Objective
Validate centralized collection and analysis of Windows security events from a Windows 11 endpoint using Wazuh SIEM/XDR in a controlled home laboratory.

## Environment
- Endpoint OS: Windows 11
- SIEM/XDR: Wazuh 4.14
- Server OS: Ubuntu Server 24.04 LTS
- Deployment: VirtualBox-based local laboratory
- Data source: Windows Event Channels
- Relevant channels: Security and Application

> Hostnames, usernames, IP addresses, credentials, and other environment-specific identifiers are intentionally omitted.

## Collection Validation
The Windows endpoint was enrolled and displayed **Active** in the Wazuh agent management interface. Threat Hunting showed records associated with the endpoint.

During a 24-hour query window, the Threat Hunting view displayed **1,168 hits**. These are query matches/alerts, **not 1,168 confirmed attacks**. The count is specific to the selected window and filters.

## Observed Events
- **Windows Event ID 4624:** Successful authentication, recorded in the Security channel.
- **Wazuh rule 60106 (level 3):** Windows Logon Success.
- **Wazuh rule 503 (level 3):** Agent started.
- **Wazuh rule 506 (level 3):** Agent stopped.
- **Wazuh rule 60642 (level 3):** Software protection service scheduled successfully.
- **Wazuh rule 19005 (level 9):** SCA/CIS benchmark summary reported a score below 30% for the applied policy.
- **Wazuh rules 19007–19009 (visible levels 3–7):** Individual SCA configuration checks.

## Interpretation
A successful authentication is not automatically suspicious. The observed SCA finding indicates a configuration/compliance gap under the applied benchmark, **not proof of compromise**. Benchmark applicability and individual failed checks should be reviewed before remediation.

## Validation Results
- Endpoint enrollment: Successful
- Agent status: Active
- Windows security events: Visible in Threat Hunting
- Authentication events: Event ID 4624 observed
- Security configuration assessment: Findings visible

## Evidence Handling
Use only sanitized screenshots. Remove endpoint names, IP addresses, usernames, record identifiers, and any credentials before publication. Do not upload raw exported event documents.

## Skills Demonstrated
Windows Event Log analysis, endpoint telemetry validation, Wazuh Threat Hunting, SIEM alert interpretation, and secure technical documentation.
