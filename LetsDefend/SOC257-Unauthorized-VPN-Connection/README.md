# SOC257 - unauthorized VPN Connection Detected 

## Scenario Overview

A security alert was triggered after a VPN login was detected from a country not authorized by the organization's access policy. The objective was to determine whether the login represented legitimate user activity or unauthorized access.

## Tools Used

* LetsDefend Platform
* VPN Authentication Logs
* IP Geolocation
* Threat Intelligence
* MITRE ATT&CK

## Investigation Steps

1. Reviewed VPN authentication logs.
2. Identified the source IP address.
3. Verified the geographic location of the login.
4. Reviewed user authentication history.
5. Checked for unusual login behavior.
6. Determined whether the login violated organizational policy.

## Findings

* VPN login originated from an unauthorized location.
* User authentication activity was reviewed.
* Alert investigated for potential unauthorized access.

## Indicators of Compromise (IOCs)

| Type      | Value    |
| --------- | -------- |
| Source IP | Redacted |
| Country   | Redacted |

## MITRE ATT&CK Mapping

* T1078 - Valid Accounts

## Outcome

The alert was investigated to determine whether it represented legitimate user activity or unauthorized account usage.

## Lessons Learned

This investigation strengthened my understanding of authentication monitoring, geolocation analysis, and identifying suspicious remote access attempts.

