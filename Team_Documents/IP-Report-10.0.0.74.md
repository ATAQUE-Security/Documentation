<img src="../assets/ring.png" width="250">

# Ataque Security

## Target

**IP Address:** 10.0.0.74

**Date, Time initial contact** E11 SEP 2023 1500hrs

**Hostname:** RISK-ANALYST1

**Purpose/Description:**

**Location:** AWS Cloud Services

**Owner/Responsible Party:** SimCorp

**Network Segment/Subnet:** 10.0.0.0/24

**Operating System:** Microsoft Windows

**Open Ports and Services:**

| Port | State | Service | Version |
|:-----------------------:|:-----------------------:|:-----------------------:|:-----------------------:|
| 135/tcp | open | msrpc | Microsoft Windows RPC |
| 139/tcp  | open | netbios-ssn | Microsoft Windows netbios-ssn |
| 445/tcp  | open | microsoft-ds | Microsoft Windows 7 - 10 microsoft-ds (workgroup: WORKGROUP) |
| 554/tcp  | open | rtsp? |:----------:|
| 2869/tcp | open | http | Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP) |
| 3389/tcp | open | ssl/ms-wbt-server? |:-----------:|
| 5357/tcp | open | http | Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP) |
| 5985/tcp | open | http | Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP) |
| 8089/tcp | open | ssl/http | Splunkd httpd |
| 10243/tcp | open | http | Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP) |
| 47001/tcp | open | http | Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP) |
| 49152/tcp | open | msrpc | Microsoft Windows RPC |
| 49153/tcp | open | msrpc | Microsoft Windows RPC |
| 49154/tcp | open | msrpc | Microsoft Windows RPC |
| 49155/tcp | open | msrpc | Microsoft Windows RPC |
| 49165/tcp | open | msrpc | Microsoft Windows RPC |
| 49167/tcp | open | msrpc | Microsoft Windows RPC |

***Include information about any non-standard or unusual services***

<br>

**Vulnerabilities/Weaknesses:**

- Port 445 (microsoft-ds) Windows file and printer sharing (SMB) and can be exploited for various attacks, including ransomware and lateral movement.

- Port 3389 (ssl/ms-wbt-server): Remote Desktop Protocol (RDP) port. Brute-force attacks and other RDP-related exploits

- Port 8089 (ssl/http Splunkd): Vulnerability Splunk configuration and exposure to the internet. Can leak sensitive information If misconfigured.

- Port 135 (msrpc) ): Microsoft Windows RPC. Vulnerabilities in the RPC service can lead to remote code execution and system compromise.

- Port 139 (netbios-ssn): NetBIOS ports various attacks, including brute force and information disclosure.

- Port 554 (rtsp): Real-Time Streaming Protocol (RTSP) vulnerability depends on the specific application using it and its configuration.

<br>

**Credentials/Authentication:**

- *Record any discovered credentials, such as usernames and passwords*

- *Specify the method used to obtain these credentials, if applicable*

<br>

**Exploits/Attacks:**

- *List any successful exploits or attacks carried out against this IP address*

- *Provide details about the exploitation process*

<br>

**Recommendations/Next Steps:**

- *Offer suggestions for remediation or mitigation measures to address vulnerabilities*

- *Include a plan for further assessment or testing, if required*

<br>

### Additional Notes

- *Add any supplementary information, observations, or context that may be relevant to this IP address*

<br>

### Revisions

- Created 9/11/2023 1800hrs. David Siebert
- Revised 9/12/2023 Raphael Chookagian

---
