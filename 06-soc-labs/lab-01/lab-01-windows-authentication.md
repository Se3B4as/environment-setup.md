# SOC Lab 01 — Windows Authentication Event Analysis

## Objective
Investigate a successful Windows authentication event collected by Wazuh and determine whether the visible fields indicate expected service activity or warrant further investigation.

## Source and Detection
- Data source: Windows Security Event Log
- Windows Event ID: **4624**
- Wazuh rule: **60106** — Windows Logon Success
- Observed Wazuh rule level: **3**
- Channel: **Security**

## Event Fields Reviewed
- `data.win.eventdata.logonType`: **5**
- `data.win.eventdata.processName`: `C:\Windows\System32\services.exe`
- `data.win.eventdata.authenticationPackageName`: `Negotiate`
- `data.win.eventdata.targetUserSid`: `S-1-5-18` (Local System)
- `data.win.eventdata.targetLogonId`: `0x3e7`
- `data.win.eventdata.keyLength`: `0`

> Usernames, hostnames, IP addresses, and other identifying fields are excluded.

## Analysis
Windows Event ID 4624 records a successful logon. **Logon Type 5** indicates a service logon rather than an interactive desktop login. The `services.exe` process and Local System SID are consistent with normal Windows service management.

The observed `keyLength` value alone does not demonstrate a security weakness. A second Event ID 4624 was also confirmed in the Security channel, but its logon type and other details were **not established** during this exercise; it is therefore not classified here.

## Preliminary Assessment
- Activity type: Service authentication
- Initial interpretation: Consistent with expected operating-system behavior
- Evidence of compromise: None identified in the reviewed fields
- Confidence: Limited to the available event data
- Status: Initial triage completed; no confirmed incident

## Lessons Learned
- Distinguish successful authentication from suspicious authentication.
- Interpret Windows logon types and account SIDs.
- Use process and event-channel context before classifying activity.
- Avoid extrapolating from one event to all logons on the endpoint.

## Evidence
Publish only a redacted screenshot of the relevant fields; do not expose endpoint or account identifiers.
