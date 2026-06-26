# SOC205 - Malicious Macro has been Executed

## Scenario Overview

A security alert indicated that a Microsoft Office document executed a potentially malicious macro. The objective was to investigate the activity, determine its impact, and identify any malicious behavior.

## Tools Used

* LetsDefend Platform
* Windows Event Logs
* VirusTotal
* MITRE ATT&CK

## Investigation Steps

1. Reviewed the security alert.
2. Identified the affected endpoint and user.
3. Examined the Office document involved.
4. Investigated macro execution activity.
5. Reviewed process execution and related events.
6. Validated indicators using available threat intelligence.

## Findings

* Malicious macro execution confirmed.
* Suspicious document identified.
* Potential malware execution activity observed.

## Indicators of Compromise (IOCs)

| Type      | Value    |
| --------- | -------- |
| File Name | Redacted |
| File Hash | Redacted |

## MITRE ATT&CK Mapping

* T1204 - User Execution
* T1059 - Command and Scripting Interpreter 

## Outcome

The alert was classified as a **True Positive** malicious macro execution incident.

## Lessons Learned

This investigation enhanced my understanding of document-based malware, macro execution risks, and endpoint investigation techniques.

