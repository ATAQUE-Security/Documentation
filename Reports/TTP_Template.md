# Overview

Perform an attack using a variety of tools and scanners you’ve studied throughout this class, then document findings in an OSCP-style report.

<br>

## Objectives

Perform enumeration and exploitation against a target system within the context of a pentest

<br>

## Resources

[Nmap scripts](https://nmap.org/)

[metasploit](https://www.metasploit.com/)

<br>

## Enumeration

<br>

### Nmap scan

![NmapScanImage]()

<br>

## Exploitation

<!-- Example: -->
### ***Vulnerability Explanation: (135/tcp msrpc - ms05_017_msmq):***

* RPC is a protocol that one program can use to request a service from a program located on another computer in a network. MSRPC is used by many Windows services, which makes it a valuable target.

### ***Vulnerability Fix:***

* **Patch the System:**
  * Ensure that the affected system is regularly updated with the latest security patches and updates from Microsoft. You can use Windows Update or Windows Server Update Services (WSUS) for this purpose.

* **Regularly Monitor for Updates:**
  * Continuously monitor for new security updates and patches released by Microsoft and apply them promptly.

* **Implement Proper Firewall Rules:**
  * Configure firewalls and network security controls to restrict access to port 135/tcp and other vulnerable services. Limit access only to authorized systems and networks.

* **Network Segmentation:**
  * Consider network segmentation to isolate critical systems and services from less critical ones. This can help contain potential security risks.

### ***Severity:*** High
<!-- Example -->

<br>

<!-- Example -->
### ***Vulnerability Explanation:***

* The vulnerability identified on port blah de blah is for this service and that exploitation, etc, murica.

### ***Vulnerability Fix:***

* **Apply Security Patch:**
  * The recommended fix is to apply the security update provided by Microsoft in MS08-067. This patch addresses the vulnerability and prevents remote code execution.

* **Intrusion Detection and Prevention:**
  * Implement intrusion detection and prevention systems (IDS/IPS) to detect and block potential exploitation attempts targeting this vulnerability.

* **Security Awareness and Training:**
  * Educate users and IT staff about the importance of security updates and the risks associated with unpatched systems.

**Severity:** High

![Image]()
<!-- Example -->
