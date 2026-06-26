# SOC176 - RDP Brute Force Detected

## Scenario Overview

A security alert indicated multiple failed Remote Desktop Protocol (RDP) authentication attempts targeting a Windows system. The objective was to investigate the activity and determine whether a brute-force attack was occurring.

## Tools Used

* LetsDefend Platform
* Windows Authentication Logs
* Event Analysis
* MITRE ATT&CK

## Investigation Steps

1. Reviewed the security alert.
2. Examined Windows authentication events.
3. Identified repeated failed login attempts.
4. Determined the targeted user account.
5. Reviewed the source IP address.
6. Evaluated attack patterns to confirm brute-force activity.

## Findings

* Multiple failed RDP login attempts identified.
* Authentication activity matched brute-force behavior.
* Targeted account and source IP were identified.

## Indicators of Compromise (IOCs)

| Type            | Value    |
| --------------- | -------- |
| Source IP       | Redacted |
| Target Username | Redacted |

## MITRE ATT&CK Mapping

* T1110 - Brute Force

## Outcome

The alert was classified as a **True Positive** brute-force attack.

## Lessons Learned

This investigation improved my understanding of Windows authentication logs, brute-force detection, and account compromise indicators.

