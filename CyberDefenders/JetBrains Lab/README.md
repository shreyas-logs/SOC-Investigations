# JetBrains — Network Forensics Investigation

> **Platform:** CyberDefenders
> **Category:** Network Forensics
> **Lab Status:** Retired
> **Primary Tool:** Wireshark
> **Investigation Type:** PCAP / Network Traffic Analysis

---

## 1. Investigation Summary

### Objective

The security incident involved an attacker successfully exploiting a vulnerability in a web server, allowing the attacker to upload webshells and gain full control over the system. The attacker utilized the compromised web server as a launch point for further malicious activities, including data manipulation.

As part of the investigation, I analyzed a packet capture (PCAP) of the network traffic to identify the methods used by the attacker. The goal was to determine the initial entry point, the attacker's tools and techniques, and the extent of the compromise.

### Environment

* **Platform:** CyberDefenders
* **Lab:** JetBrains
* **Category:** Network Forensics
* **Tool(s):** Wireshark
* **Evidence:** Network packet capture (PCAP)

### Summary of Findings

Based on my investigation, I found that an attacker exploited the vulnerability to gain full control over the system and used the compromised server to modify files through unauthorized activity.

---

## 2. Methodology

The investigation was performed using the following approach:

### 2.1 Initial PCAP Analysis

* Loaded the PCAP into Wireshark.
* Reviewed overall packet/protocol distribution.
* Identified relevant network protocols.
* Examined communicating hosts and IP addresses.

### 2.2 Traffic Filtering

I used the following Wireshark filter to identify HTTP POST requests:

```text
http.request.method == POST
```

### 2.3 HTTP / Network Traffic Analysis

To identify the attacker's source IP address, I performed traffic filtering.

* **Source IP:** `23.158.56.196`
* **Destination IP:** `172.31.25.119`
* **Request:** `POST`

**Relevant observation:** The POST request information was not `application/x-www-form-urlencoded`; instead, it showed a ZIP file.

### 2.4 Traffic Correlation

I connected multiple packets and related HTTP requests to narrow down the investigation. By correlating the traffic, I identified evidence related to the files involved and determined the ZIP file name.

---

## 3. Evidence

The following evidence supported the investigation findings.

### Evidence 1 — Suspicious POST Request from 23.158.56.196

**Observation:**

Based on the investigation, an attacker uploaded the ZIP file via a webshell.

**Wireshark filter:**

```text
http.request.method == POST
```

This filter was used to identify the suspicious POST request.

**Relevant details:**

* **Source IP:** `23.158.56.196`
* **Destination IP:** `172.31.25.119`
* **Request:** `POST`
* **Port:** `8111`

---

### Evidence 2 — CVE Corresponding to the Exploited Vulnerability

**Observation:**

I performed OSINT research to identify the CVE corresponding to the vulnerability the attacker exploited. Before identifying the CVE, I first needed to determine the web-server version.

**Wireshark filter:**

### Evidence 3 — Account Created After the Attack

**Observation:**

An attacker created a user account after exploiting the vulnerability and configured credentials for the account.

---

## 4. Findings

### Finding 1 — User Account Name and Password

**What was observed:**

I observed that the attacker set up the username `c91oyemw` and password `CL5vzdwLuK`.

**Analysis:**

It was important to identify the credentials the attacker configured after creating a new user account because the account was associated with subsequent data manipulation activity.

**Evidence:**

This finding is supported by the account-creation evidence identified during the investigation.

---

### Finding 2 — Command Execution and Tampered Text File

**What was observed:**

I identified the date and time when the attacker executed the first command and tampered with a text file containing the credentials of the web-server administrator. The attacker modified the credentials contained in the file.

**Analysis:**

The evidence indicated that the web server was compromised through a webshell. The attacker subsequently accessed confidential data and modified a file containing administrator credentials.

**Evidence:**

The activity was identified by correlating HTTP POST requests from the attacker source IP with the webshell URI.

---

### Finding 3 — Container Escape Attempt

**What was observed:**

The attacker attempted to escape from the container by executing the following command:

```text
docker run --rm -it -v /:/host ubuntu chroot /host
```

The attempt was unsuccessful.

**Analysis:**

The command demonstrated an attempt to escape from the compromised container and access the host filesystem.

---

## 5. Indicators of Compromise (IOCs)

| Type       | Indicator                                             | Context                             |
| ---------- | ----------------------------------------------------- | ----------------------------------- |
| IP Address | `23.158.56.196`                                       | Source IP address                   |
| URL        | `http://3.71.79.4:8111/plugins/NSt8bHTg/NSt8bHTg.jsp` | Webshell URL                        |
| Filename   | `NSt8bHTg.zip`                                        | ZIP file associated with the attack |

> Only indicators identified during the investigation are included.

---

## 6. Lessons Learned

This investigation helped reinforce the following skills:

* PCAP analysis using Wireshark
* Network traffic filtering
* HTTP/network protocol analysis
* Identifying suspicious network communication
* Following HTTP streams
* Extracting indicators of compromise
* Correlating network evidence to determine activity
* Documenting investigation findings

### Key Takeaways

* Used Wireshark to analyze network traffic and identify suspicious HTTP POST requests.
* Correlated multiple packets to identify attacker activity and files involved in the attack.
* Practiced extracting indicators of compromise from network traffic.
* Investigated attacker behavior including webshell activity, credential manipulation, and a container escape attempt.

---

## Tools Used

* **Wireshark**
* **OSINT research**

---

## Disclaimer

This write-up is based on a retired CyberDefenders training lab and represents my own analysis and investigation notes. Challenge files and proprietary lab content are not redistributed.

