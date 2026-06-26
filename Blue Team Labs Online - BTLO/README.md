# BTLO - RDP Brute Force Investigation

## Scenario Overview

A Windows Security Event Log containing a large number of Audit Failure events was provided as part of a Blue Team Labs Online (BTLO) challenge. The objective was to analyze the log data, identify evidence of an attempted Remote Desktop Protocol (RDP) brute-force attack, and answer investigation questions based on the collected evidence.

## Objective

Investigate Windows Security Event Logs to determine:

* Source IP address responsible for the attack
* Targeted user account(s)
* Authentication failure patterns
* Indicators of brute-force activity
* Timeline of the attack

## Evidence Provided

* Windows Security Event Log
* Investigation Questions
* Supporting challenge artifacts

## Tools Used

* Windows Event Viewer
* Windows Command Line
* Log Analysis Techniques
* Event ID Analysis
* VirusTotal (where applicable)

## Investigation Process

1. Examined the provided evidence package.
2. Loaded and reviewed Windows Security Event Logs.
3. Filtered relevant authentication events.
4. Identified repeated failed logon attempts.
5. Correlated Event IDs and timestamps.
6. Determined the source IP address responsible for the attack.
7. Identified targeted user account(s).
8. Built the attack timeline.
9. Answered challenge questions using collected evidence.

## Key Findings

* Multiple failed RDP authentication attempts identified.
* Source IP address successfully identified.
* Targeted Windows account(s) determined.
* Attack pattern confirmed as a brute-force attempt.
* Timeline of malicious activity established.

## MITRE ATT&CK Mapping

* T1110 - Brute Force
* T1021.001 - Remote Services: Remote Desktop Protocol

## Skills Demonstrated

* Windows Event Log Analysis
* Authentication Log Investigation
* Timeline Analysis
* IOC Identification
* Evidence Correlation
* Incident Investigation

## Lessons Learned

This investigation strengthened my understanding of Windows authentication logs, Event ID analysis, brute-force attack detection, and evidence-based incident investigation using real log artifacts.

