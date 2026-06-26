# SOC282 - Phishing Alert - Deceptive Mail Detected

## Scenario Overview

A security alert was generated after a suspicious email was detected within the organization's Microsoft Exchange environment. The objective was to investigate the email, determine whether it was malicious, and identify any indicators of compromise.

## Tools Used

* LetsDefend Platform
* Email Header Analysis
* VirusTotal
* URL & Domain Analysis
* MITRE ATT&CK

## Investigation Steps

1. Reviewed the alert details and affected user.
2. Examined the sender's email address and email headers.
3. Analyzed embedded URLs and attachments.
4. Checked sender reputation and domain information.
5. Validated indicators using threat intelligence sources.
6. Determined whether the alert represented a phishing attempt.

## Findings

* Suspicious email confirmed.
* Malicious indicators identified within the email.
* Alert classified as a phishing attack.

## Indicators of Compromise (IOCs)

| Type         | Value    |
| ------------ | -------- |
| Sender Email | Redacted |
| URL          | Redacted |
| Domain       | Redacted |

## MITRE ATT&CK Mapping

* T1566 - Phishing

## Outcome

The alert was classified as a **True Positive** phishing incident.

## Lessons Learned

This investigation improved my understanding of email security analysis, phishing detection techniques, and validating malicious indicators using threat intelligence.

