# Overview

Perform an attack using a variety of tools and scanners you’ve studied throughout this class, then document findings in an OSCP-style report.

<br>

## Objectives

Perform enumeration and exploitation against a target system within the context of a pentest

<br>

## Resources

[Nmap scripts]()

[metasploit]()

<br>

## Enumeration

<br>

### Nmap scan

![NmapScanImage]()

<br>

## Exploitation

Vulnerability Explanation: (135/tcp msrpc - ms05_017_msmq): RPC is a protocol that one program can use to request a service from a program located on another computer in a network. MSRPC is used by many Windows services, which makes it a valuable target.

Vulnerability Fix:

Patch the System: Ensure that the affected system is regularly updated with the latest security patches and updates from Microsoft. You can use Windows Update or Windows Server Update Services (WSUS) for this purpose.
Regularly Monitor for Updates: Continuously monitor for new security updates and patches released by Microsoft and apply them promptly.
Implement Proper Firewall Rules: Configure firewalls and network security controls to restrict access to port 135/tcp and other vulnerable services. Limit access only to authorized systems and networks.
Network Segmentation: Consider network segmentation to isolate critical systems and services from less critical ones. This can help contain potential security risks.

Severity: High

Searching Metasploit for possible exploits and scripts to run.

MS08-067 Vulnerability:
A critical vulnerability in the Windows Server service. If successfully exploited, it allows for remote code execution. An attacker who successfully exploited this vulnerability could take complete control of an affected system. The WannaCry ransomware notably exploited systems that were vulnerable to this flaw.

![NmapScanImage]()

<br>

Vulnerability Explanation: (135/tcp msrpc - ms08-067netapi):
The vulnerability identified on port 135/tcp related to MSRPC (Microsoft Remote Procedure Call) with the reference "ms08-067netapi" is associated with a critical security issue. This vulnerability is specifically related to Microsoft Security Bulletin MS08-067, which addressed a critical remote code execution vulnerability in the Windows Server service.

Vulnerability Fix:
Apply Security Patch: The recommended fix is to apply the security update provided by Microsoft in MS08-067. This patch addresses the vulnerability and prevents remote code execution.
Intrusion Detection and Prevention: Implement intrusion detection and prevention systems (IDS/IPS) to detect and block potential exploitation attempts targeting this vulnerability.
Security Awareness and Training: Educate users and IT staff about the importance of security updates and the risks associated with unpatched systems.

Severity: High

![Image]()

<br>

Tried a simple rcpclient login just to cover all the bases.

Vulnerability Explanation: (135/tcp msrpc - rcpclient): is used for Microsoft Remote Procedure Call, which is a protocol used by Windows systems for communication between processes on a network. Vulnerabilities associated with port 135/tcp msrpc can vary widely, including buffer overflows, denial-of-service (DoS) attacks, and remote code execution vulnerabilities.

Vulnerability Fix:
The primary way to mitigate vulnerabilities associated with port 135/tcp msrpc is to ensure that affected Windows systems are regularly updated with the latest security patches and updates from Microsoft. Use Windows Update or Windows Server Update Services (WSUS) for this purpose.

Severity: High

![Image]()

<br>

Vulnerability Explanation: (139/tcp netbios): Vulnerabilities associated with port 139/tcp NetBIOS can include unauthorized access, information disclosure, and remote code execution vulnerabilities. Exploiting these vulnerabilities can allow attackers to gain unauthorized access to Windows systems, extract sensitive information, or execute arbitrary code on the target system.

Vulnerability Fix:
Firewall Rules: Configure firewalls and network security controls to restrict access to port 139/tcp NetBIOS and other vulnerable services. Limit access only to authorized systems and networks.
Security Best Practices: Follow security best practices for system hardening and configuration to minimize exposure to known vulnerabilities.
Network Segmentation: Consider network segmentation to isolate critical systems and services from less critical ones. This can help contain potential security risks.
Vulnerability Scanning: Regularly perform vulnerability scanning and assessments on your network to identify and remediate potential vulnerabilities.

Severity: High

Enumerate SMB for Port 139 - NetBios

`Enum4linux -a <Target IP>`

![Image]()

<br>

Nmap using a script to enumerate SMB

`nmap -p 139,445 --script smb-enum-shares,smb-enum-users <Target IP>`

![Image]()

<br>

Metasploit to scan for SMB version:

![Image]()

<br>

Vulnerability Explanation:(139,445/tcp msrpc - EternalBlue): The "EternalBlue" vulnerability, often associated with ports 139/tcp and 445/tcp (which are typically used for Microsoft File and Printer Sharing), is a critical security issue that gained notoriety due to its role in the WannaCry ransomware attack.

Vulnerability Fix:
Microsoft released a security update (MS17-010) to address the EternalBlue vulnerability. The primary mitigation for this vulnerability is to ensure that all Windows systems on your network are patched with the necessary security updates. Use Windows Update, Windows Server Update Services (WSUS), or other update management solutions to deploy these updates.

Severity: High

Using Metasploit to check for the EternalBlue Exploit

![Image]()

<br>

Vulnerability Explanation: (554/tcp rtpc) Vulnerabilities associated with port 554/tcp RTSP can include unauthorized access, information disclosure, and potential remote code execution vulnerabilities.Exploiting these vulnerabilities can allow attackers to gain unauthorized access to streaming media servers, extract sensitive information, or execute arbitrary code on the target system.

Vulnerability Fix:
Applying security updates and patches to streaming media servers and related software.
Configuring proper access controls and authentication mechanisms to restrict unauthorized access to streaming resources.
Employing network security controls, such as firewalls, to control and monitor traffic on port 554/tcp.

Severity: High

`Sudo nmap -p 554 --script=banner <Target IP>`

![Image]()

Nikto is a web server scanner that detects vulnerabilities and misconfigurations.

![Image]()

<br>

Vulnerability Explanation: (2869/tcp http): Port 2869/tcp is commonly associated with UPnP services, which facilitate automatic discovery and configuration of devices on a network. Vulnerabilities in UPnP implementations can potentially allow attackers to exploit weaknesses in the service, leading to unauthorized access, information disclosure, or other security issues.

Vulnerability Fix:
Applying security updates and patches provided by the device manufacturer or software vendor.
Disabling UPnP if it is not essential for network functionality, as UPnP introduces potential security risks.
Configuring network firewalls and access controls to restrict access to UPnP services from untrusted sources.
Regularly monitoring network traffic and device logs for suspicious activity.

Severity: High

Dirb is a tool to discover directories and files on web servers.

![Image]()

<br>

Vulnerability Explanation: (3389/rdp) Vulnerabilities in RDP implementations can potentially allow attackers to exploit weaknesses in the service, leading to unauthorized access, remote code execution, information disclosure, or other security issues.

Vulnerability Fix:
Applying security updates and patches provided by Microsoft for the Windows operating system.
Configuring strong authentication mechanisms and access controls to restrict RDP access to authorized users.
Regularly monitoring RDP access logs and implementing intrusion detection systems to detect and respond to suspicious activity.

Severity: High

This command checks for the RDP encryption level and tests for the known MS12-020 vulnerability.

`nmap -p 3389 --script rdp-enum-encryption,rdp-vuln-ms12-020 10.0.0.74`

![Image]()

Using Hydra to bruteforce attack RDP

`sudo hydra -t 1 -V -f -L /usr/share/wordlists/seclists/Usernames/cirt-default-usernames.txt -P /usr/share/wordlists/seclists/Passwords/2020-200_most_used_passwords.txt rdp://10.0.0.74`

![Image]()
![Image]()

<br>
<br>
