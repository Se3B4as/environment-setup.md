# Wazuh Threat Hunting — Initial Alert Review

## Purpose
Review endpoint alerts in Wazuh Threat Hunting and distinguish operational events, authentication activity, and security configuration findings.

## Method
1. Open Wazuh Dashboard → Threat Hunting.
2. Select a 24-hour time range.
3. Scope results to the enrolled Windows endpoint.
4. Review timestamp, `rule.description`, `rule.level`, and `rule.id`.
5. Open individual records to examine Windows event metadata and context.

## Observations
- **1,168 hits** appeared in the observed 24-hour query window.
- Authentication success alerts were visible (`rule.id: 60106`, level 3).
- Wazuh agent start and stop events were visible (`503`, `506`, level 3).
- Windows software protection service scheduling events were visible (`60642`, level 3).
- A CIS benchmark/SCA summary was visible (`19005`, level 9), reporting a score below 30% under the applied benchmark.
- Several individual benchmark configuration checks were visible (`19007`, `19008`, `19009`).

## Analysis
The alert set included routine system activity as well as configuration findings requiring separate review. The count represents matched records, not confirmed malicious activity. A rule level helps prioritize review but does not independently establish incident severity.

## Investigation Workflow
- Confirm source endpoint and event channel.
- Identify Windows Event ID and event-specific fields.
- Correlate related events by time and process when possible.
- Document evidence, uncertainties, and preliminary classification.
- Avoid declaring a security incident without supporting evidence.

## Outcome
Centralized alert visibility was verified. A Windows service logon event was selected for detailed authentication analysis; a separate .NET Runtime application error was also identified for triage.

## Evidence
Sanitized screenshots may be stored under the repository's screenshot directory and linked here. No raw identifiers or secrets should be published.
