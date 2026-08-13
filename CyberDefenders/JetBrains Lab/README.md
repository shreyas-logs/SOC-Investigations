JetBrains — Network Forensics Investigation

Platform: CyberDefenders
Category: Network Forensics
Lab Status: Retired
Primary Tool: Wireshark
Investigation Type: PCAP / Network Traffic Analysis

1. Investigation Summary
Objective
     The security incident is about an attacker successfully exploited a vulnerability in web server, allowing to upload webshells and gain full control over the system. The attacker utilized the compromised web server as a launch point for further malicious activities, including data manipulation. 
As part of the investigation, a packet capture (PCAP) file of the network traffic provided and identify the methods used by the attacker. The goal is to determine the initial entry point, the attacker's tools and techniques, and the compromise's extent.

Environment
Platform: CyberDefenders
Lab: JetBrains
Category: Network Forensics
Tool(s): Wireshark
Evidence: Network packet capture (PCAP)
Summary of Findings
        Based on my investigation, i found out that an attacker exploited the vulnerability to gain full control over the system and used the compromised server to modify the files by      unauthorized way.

2. Methodology

The investigation was performed using the following approach:

2.1 Initial PCAP Analysis

Loaded the PCAP into Wireshark.
Reviewed overall packet/protocol distribution.
Identified relevant network protocols.
Examined communicating hosts and IP addresses.

2.2 Traffic Filtering
    http.request.method == POST 

2.3 HTTP / Network Traffic Analysis

First of all to find the attackers source IP address i perform traffic filtering 

Source IP: 23.158.56.196
Destination IP:172.31.25.119
Request: POST   
Relevant observation: The POST request info was not (application/w-xxx-form-urlencoded) but showing a zip File 

2.5 Traffic Correlation
     I connected multiple packets/events to reach your conclusion
            After started to investigation the packets i narrow down the search with connecting multiple packets to find evidence related within files and also find out the ZIP file name       

3. Evidence

The following evidence supported the investigation findings.

Evidence 1 — The Suspicious Info about the POST request made by 23.158.56.196 Source IP address

Observation:
         based on the investigation an attacker uploaded the ZIP file via webshell

Wireshark filter: 

http.request.method == POST - found supicipus POST request

Relevant details:

Source IP: 23.158.56.196
Destination IP:172.31.25.119
Request: POST
Port: 8111


Evidence 2 —  CVE number corresponds to the vulnerability the attacker exploited

Observation:

I did OSINT to find out the CVE number correspond to vulnerabilty the attacker exploited 
but before that I need to find out the Webserver version 


Evidence 3 — Created account after an attack

Observation: an attacker created a user account after exploited a vulnerability and sets up the credentials


4. Findings

Finding 1 — User account name and password

What was observed: we observed that an attacker sets up c91oyemw & CL5vzdwLuK this username and password

Analysis:

   I analyse that it was important to know about the credentials he set up after creating an new user account which leads to data manipulation



Finding 2 — Command Execution and tampered text file 

What was observed: I observed the date and time when an attacker execute its first command and tampered with a text file that contains the credentials of admin user of webserver and modify the credetials 

Wireshark Command : ip.src == 23.158.56.196 && http.request.method == POST && http.request.uri contains NSt8bHTg.jsp

Changed Username and password - a1l4m & youarecompromised

Analysis: I analyse that the exploitation of webserver was done by webshell to compromised the the confidential data and tampered with a file and modifies it 

Finding 3 — attacker tried to escape but didn’t succeed, 

What was observed: The attacker tried to escape from the container by executing a command docker run --rm -it -v /:/host ubuntu chroot /host but he didn’t succeed 


[Explain your analysis.]

5. Indicators of Compromise (IOCs)
Type	Indicator	Context
IP Address	23.158.56.196	- src ip address
URL	http://3.71.79.4:8111/plugins/NSt8bHTg/NSt8bHTg.jsp
Filename:	NSt8bHTg.zip

Only indicators identified during the investigation are included.

6. Lessons Learned

This investigation helped reinforce the following skills:

PCAP analysis using Wireshark
Network traffic filtering
HTTP/network protocol analysis
Identifying suspicious network communication
Following HTTP streams
Extracting indicators of compromise
Correlating network evidence to determine activity
Documenting investigation findings
Key Takeaways


Disclaimer:
This write-up is based on a retired CyberDefenders training lab and represents my own analysis and investigation notes. Challenge files and proprietary lab content are not redistributed.
