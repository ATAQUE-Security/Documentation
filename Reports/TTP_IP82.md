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
### ***Vulnerability Explanation: (21/tcp ftp):***

* Port 21 is running an FTP (File Transfer Protocol) service. FTP is a network protocol commonly used for transferring files between a client and a server. The presence of an open FTP port represents a potential security risk if not properly configured and secured.

### ***Vulnerability Fix:***

* **EAccess Control:**
  * Restrict access to the FTP server by allowing only authorized users or IP addresses to connect. Implement strong password policies and use multi-factor authentication (MFA) if possible.

* **Encryption:**
  * Enable secure FTP protocols like FTPS (FTP Secure) or SFTP (SSH File Transfer Protocol) to encrypt data in transit, preventing eavesdropping and data interception.

* **Implement Proper Firewall Rules:**
  * Configure firewall rules to limit incoming and outgoing traffic on port 21 and any additional ports used by the FTP service. Only allow necessary traffic.

* **Regular Auditing:**
  * Conduct regular security audits and vulnerability assessments to identify and address any weaknesses in the FTP service configuration.

### ***Severity:*** High

![FTP 10.0.0.82]()

![hydra -l Administrator -P /usr/share/wordlists/rockyou.txt ftp://<TargetIP> -t 4]()

<br>

### ***Vulnerability Explanation: (80/tcp http):***

* Port 80 is running an HTTP (Hypertext Transfer Protocol) service. HTTP is the foundation of data communication on the World Wide Web and is commonly used for serving web pages and other resources over the internet. An open port 80 represents the presence of a web server on the target system.

### ***Vulnerability Fix:***

* **Web Application Firewall (WAF):**
  * Consider using a Web Application Firewall to filter and monitor incoming web traffic for suspicious or malicious behavior. A WAF can help block known attack patterns.

* **Regular Backups:**
  * Regular Backups: Maintain up-to-date backups of web server data and configurations. Regularly test the restoration process to ensure data can be recovered in the event of a compromise.

* **Logging and Monitoring:**
  * Enable logging for the web server and regularly review logs for signs of suspicious activities. Implement intrusion detection systems (IDS) and intrusion prevention systems (IPS) to detect and block malicious traffic.

**Severity:** High

Why is image cut in half? Check/inspect page
![http://localhost:80]()

I recognize this image and name, maybe from codefellows/slack, maybe from Linkedin? Both?

![http://localhost/david.jpg]()

Downloaded image, checked properties, check these hashes?

![Downloaded Image and hashes]()

Found him on Linkedin, this might be something to look further into, or it might be a decoy.

[David Lee Linkedin](https://www.linkedin.com/in/david-lee-itpro/)

![Previous Instructor at CodeFellows and currently AWS Security Engineer]()

![Github]()

<br>

### ***Vulnerability Explanation: (135/tcp msrpc):***

* Port 135 is running the MSRPC (Microsoft Remote Procedure Call) service. MSRPC is a Microsoft technology that enables remote procedure calls between applications and services on a Windows-based system. While MSRPC itself is a legitimate protocol, it has historically been associated with vulnerabilities and security issues.

### ***Vulnerability Fix:***

* To mitigate this vulnerability, it is crucial to apply and consistently maintain the most current security updates for the underlying operating system, especially if the system is running a Microsoft Windows operating system. Regular updates help patch known security vulnerabilities and enhance the overall security of the system.

**Severity:** High

<br>

### ***Vulnerability Explanation: (139/tcp netbios):***

* Port 139 is associated with the NetBIOS (Network Basic Input/Output System) service. NetBIOS is an older networking protocol used for communication between devices on a local network. While it has legitimate uses, it has also been historically linked to significant security vulnerabilities and risks.

### ***Vulnerability Fix:***

* To mitigate this vulnerability, it is imperative to apply and consistently maintain the most current security updates for the underlying operating system and network devices. Regular updates help patch known security vulnerabilities and enhance the overall security of the system.

**Severity:** High

<br>

### ***Vulnerability Explanation: (139,445/tcp msrpc - EternalBlue):***

* Ports 139 and 445, both associated with the Microsoft Remote Procedure Call (MSRPC) service, are vulnerable to the EternalBlue exploit. EternalBlue is a well-known and highly critical vulnerability that targets Windows operating systems. This vulnerability allows remote attackers to execute arbitrary code on a target system without user interaction, potentially leading to complete system compromise.

### ***Vulnerability Fix:***

* To mitigate this vulnerability, it is essential to apply and consistently maintain the most current security updates provided by Microsoft. Microsoft released patches specifically addressing the EternalBlue vulnerability in response to its discovery.

**Severity:** High

Using Metasploit to check for the EternalBlue Exploit

![EternalBlue Metasploit]()

<br>

### ***Vulnerability Explanation: (3389/tcp - ssl/ms-wbt-server):***

* Port 3389 (TCP) running the SSL/MS-WBT-Server service is vulnerable to potential security threats. This port is commonly associated with the Microsoft Remote Desktop Protocol (RDP) service, which allows remote desktop access to Windows systems. Vulnerabilities in the RDP service can pose significant risks to the security of the system.

### ***Vulnerability Fix:***

* To mitigate this vulnerability, it is crucial to apply and consistently maintain the most current security updates provided by Microsoft. Microsoft periodically releases patches to address known vulnerabilities and enhance the security of the RDP service.

**Severity:** High

[HackTricks_PenTesting_RDP](https://book.hacktricks.xyz/network-services-pentesting/pentesting-rdp)

It checks the available encryption and DoS vulnerability (without causing DoS to the service) and obtains NTLM Windows info (versions).

`nmap --script "rdp-enum-encryption or rdp-vuln-ms12-020 or rdp-ntlm-info" -p 3389 -T4 <TargetIP>`

![nmap scan]()

` hydra -L /usr/share/seclists/Usernames/top-usernames-shortlist.txt -P /usr/share/seclists/Passwords/500-worst-passwords.txt 10.0.0.82 rdp `

![Hydra]()

<br>

### ***Vulnerability Explanation: 5985/tcp(http):***

* Windows Management Instrumentation is a service that enables both local and remote access, though the latter is facilitated by Remote Services such as Distributed Component Object Model (DCOM) and Windows Remote Management (WinRM). An adversary can use WMI to interact with local and remote systems and use it as a means to execute various behaviors, such as gathering information for Discovery as well as remote Execution of files as part of Lateral Movement.

### ***Vulnerability Fix:***

* Apply and maintain the most current security updates.

* M1040: Behavior Prevention on Endpoint

* M1038: Execution Prevention

* M1026: Privileged Account Management

* M1018: User Account Management

**Severity:** High

<br>

### ***Vulnerability Explanation: (47001/tcp http):***

* Port 47001 (TCP) running the HTTP service is potentially vulnerable to security threats. HTTP is a common protocol used for web services and applications. This vulnerability may expose the web server or application running on this port to potential risks.

### ***Vulnerability Fix:***

* To mitigate this vulnerability, it is essential to apply and consistently maintain the most current security updates for both the web server software and any hosted web applications. This includes regularly patching and updating the server's operating system, web server software (e.g., Apache, Nginx), and any application frameworks or libraries in use.

**Severity:** High

<br>

### ***Vulnerability Explanation: (47001/tcp http):***

* Port 49154 (TCP) running the msrpc service is potentially vulnerable to security threats. MSRPC (Microsoft Remote Procedure Call) is a protocol used for communication between Windows systems. This vulnerability may expose the service using msrpc on this port to potential risks.

### ***Vulnerability Fix:***

* To mitigate this vulnerability, it is crucial to apply and consistently maintain the most current security updates for the system or service using msrpc on port 49154. This includes regularly updating the Windows operating system and any software or applications that rely on msrpc.

**Severity:** High
