<p style="text-align: right">
September 11, 2023</p>

<img src="../assets/ring.png" width="250">

# **ATAQUE SECURITY**

## **Penetration Test Report for SimCorp**

[Google_Docs_Report](https://docs.google.com/document/d/1CDvXPxfJEOHXxPF0aDLlPLerwZEV6g_lDtjprG_z0RI/edit?usp=sharing)

<br>

<br>

**Introduction**

Welcome to the comprehensive penetration test report for SimCorp. This document encapsulates the exhaustive efforts undertaken by ATAQUE Security in evaluating the security posture of SimCorp's networks and systems. All activities detailed herein were performed under authorized and contractual conditions.

**Objective**

The focal point of this assessment revolves around executing an internal penetration test targeting SimCorp's internal network. ATAQUE Security is responsible for the complete lifecycle of this assessment - from initial testing and auditing to the final reporting. We strictly adhered to the established guidelines and parameters, ensuring a controlled yet robust evaluation environment.

Key Task:

* Enumerate and exploit target systems within the boundaries of a penetration test.

**High-Level Summary**

Tasked with a crucial mission, ATAQUE Security embarked on an internal penetration test aimed at SimCorp's infrastructure. The primary goal was to simulate potential adversarial actions: mapping the network, identifying connected systems, exploiting detected vulnerabilities, and then channeling these findings to inform defensive measures.

Key Outcomes:

* Vulnerabilities Unearthed: Throughout the penetration test, several critical vulnerabilities came to light.

* Access Gained: Successful exploitation led to unauthorized access to multiple assets, including databases, file shares, and servers.

* Root Causes: A significant portion of the vulnerabilities could be attributed to outdated software patches and suboptimal security configurations.

As we progress through the report, each target will be examined in detail, shedding light on specific vulnerabilities, exploitation methods, and recommended remediation steps. It is our hope that this report serves not just as a record of findings but as a roadmap for fortifying SimCorp's digital assets.

<br>
<br>

## Open Ports from standard Nmap scan

<table>
  <tr>
   <td><strong>Target IP: 10.0.0.74</strong>
   </td>
   <td><strong>Target IP: 10.0.0.82</strong>
   </td>
   <td><strong>Target IP: 10.0.123</strong>
   </td>
  </tr>
  <tr>
   <td><em>135/tcp - msrpc</em>
   </td>
   <td><em>21/tcp - ftpd</em>
   </td>
   <td><em>22/tcp - ssh</em>
   </td>
  </tr>
  <tr>
   <td><em>139/tcp - netbios-ssn</em>
   </td>
   <td><em>80/tcp - http</em>
   </td>
   <td><em>111/tcp - rpcbind</em>
   </td>
  </tr>
  <tr>
   <td><em>445/tcp - microsoft-ds</em>
   </td>
   <td><em>135/tcp - msrpc</em>
   </td>
   <td><em>2049/tcp - nfs</em>
   </td>
  </tr>
  <tr>
   <td><em>554/tcp - rtsp</em>
   </td>
   <td><em>139/tcp - netbios-ssn</em>
   </td>
   <td><em>8089/tcp - ssl/http</em>
   </td>
  </tr>
  <tr>
   <td><em>2869/tcp - http</em>
   </td>
   <td><em>445/tcp - microsoft-ds</em>
   </td>
   <td>
   </td>
  </tr>
</table>

<br>

<table>
  <tr>
   <td><strong>Target IP: 10.0.0.126</strong>
   </td>
   <td><strong>Target IP: 10.0.0.175</strong>
   </td>
   <td><strong>Target IP: 10.0.0.197</strong>
   </td>
   <td><strong>Target IP: 10.0.0.206</strong>
   </td>
  </tr>
  <tr>
   <td><em>135/tcp - msrpc</em>
   </td>
   <td><em>22/tcp - ssh</em>
   </td>
   <td><em>135/tcp - msrpc</em>
   </td>
   <td><em>135/tcp - msrpc</em>
   </td>
  </tr>
  <tr>
   <td><em>139/tcp - netbios-ssn</em>
   </td>
   <td><em>80/tcp - http</em>
   </td>
   <td><em>139/tcp - netbios-ssn</em>
   </td>
   <td><em>139/tcp - netbios-ssn</em>
   </td>
  </tr>
  <tr>
   <td><em>445/tcp - microsoft-ds</em>
   </td>
   <td><em>8089/tcp - ssl/http</em>
   </td>
   <td><em>445/tcp - microsoft-ds</em>
   </td>
   <td><em>445/tcp - microsoft-ds</em>
   </td>
  </tr>
  <tr>
   <td><em>3389/tcp - ms-wbt-server</em>
   </td>
   <td>
   </td>
   <td><em>3389/tcp - ms-wbt-server</em>
   </td>
   <td><em>3389/tcp - ms-wbt-server</em>
   </td>
  </tr>
  <tr>
   <td><em>5985/tcp - http</em>
   </td>
   <td>
   </td>
   <td><em>8089/tcp - ssl/http</em>
   </td>
   <td><em>8089/tcp - ssl/http</em>
   </td>
  </tr>
</table>

<br>

**Recommendations**

ATAQUE Security recommends patching the vulnerabilities identified during the testing to ensure that attackers cannot exploit these systems in the future. It is important to note these systems require frequent patching and once patched, should remain on a regular patch program to protect additional vulnerabilities that are discovered at a later date.

<br>

**Information Gathering**

The information gathering portion of a penetration test focuses on identifying the scope of the penetration test. During this penetration test, ATAQUE was tasked with exploiting the Lab network. The specific IP addresses were:

* **10.0.0.74**
* **10.0.0.82**
* **10.0.0.123**
* **10.0.0.126**
* **10.0.0.175**
* **10.0.0.197**
* **10.0.0.206**

<br>

**Penetration**

The penetration testing portions of the assessment focus heavily on gaining access to a variety of systems. During this penetration test, we were able to successfully gain access to X out of the X systems.

* **System IP: 10.0.0.74**
* **System IP: 10.0.0.82**
* **System IP: 10.0.0.123**
* **System IP: 10.0.0.126**
* **System IP: 10.0.0.175**
* **System IP: 10.0.0.197**
* **System IP: 10.0.0.206**

<br>
<br>

**Service Enumeration**

The service enumeration portion of a penetration test focuses on gathering information about what services are alive on a system or systems. This is valuable for an attacker as it provides detailed information on potential attack vectors into a system. Understanding what applications are running on the system gives an attacker needed information before performing the actual penetration test.  In some cases, some ports may not be listed.

<br>
<br>

**Nmap scan report for 10.0.0.74**

[Full Report Target IP: 10..0.0.74](https://docs.google.com/document/d/1TtLq0CBkvyH8kMP8KOGDAZ98rvfBKD44Sx3vE9UmfpQ/edit?usp=sharing)

* Host is up (0.025s latency).
* Not shown: 65518 closed tcp ports (reset)
* Service Info: Host: RISK-ANALYST1; OS: Windows; CPE: cpe:/o:microsoft:windows

<table>
  <tr>
   <td>
<strong>Port:</strong>
   </td>
   <td><strong>State:</strong>
   </td>
   <td><strong>Service:</strong>
   </td>
   <td><strong>Version:</strong>
   </td>
  </tr>
  <tr>
   <td>135/tcp
   </td>
   <td>open
   </td>
   <td> msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>139/tcp
   </td>
   <td>open
   </td>
   <td>netbios-ssn
   </td>
   <td>Microsoft Windows netbios-ssn
   </td>
  </tr>
  <tr>
   <td>445/tcp
   </td>
   <td>open
   </td>
   <td>microsoft-ds
   </td>
   <td>Microsoft Windows 7 - 10 microsoft-ds (workgroup: WORKGROUP)
   </td>
  </tr>
  <tr>
   <td>554/tcp
   </td>
   <td>open
   </td>
   <td>rtsp
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>2869/tcp
   </td>
   <td>open
   </td>
   <td>http
   </td>
   <td>Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
   </td>
  </tr>
  <tr>
   <td>3389/tcp
   </td>
   <td>open
   </td>
   <td>ssl/ms-wbt-server
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>5357/tcp
   </td>
   <td>open
   </td>
   <td>http
   </td>
   <td>Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
   </td>
  </tr>
  <tr>
   <td>10243/tcp
   </td>
   <td>open
   </td>
   <td>http
   </td>
   <td>Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
   </td>
  </tr>
  <tr>
   <td>47001/tcp
   </td>
   <td>open
   </td>
   <td>ssl/http
   </td>
   <td>Splunkd httpd
   </td>
  </tr>
  <tr>
   <td>49152/tcp open  msrpc
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>49153/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>49154/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>49155/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>49165/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>49167/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
</table>

<br>
<br>

**Nmap scan report for 10.0.0.82**

[Full Report Target IP: 10.0.0.82](https://docs.google.com/document/d/1VmOQK37F_Ffnw8VyKxtWDHrs2pfVXO6_O4nqDzJOXGM/edit?usp=sharing)

* Host is up (0.024s latency).
* Not shown: 65521 closed tcp ports (reset)
* Service Info: Host: OS: Windows; CPE: cpe:/o:microsoft:windows

<table>
  <tr>
   <td>
<strong>Port:</strong>
   </td>
   <td><strong>State:</strong>
   </td>
   <td><strong>Service:</strong>
   </td>
   <td><strong>Version:</strong>
   </td>
  </tr>
  <tr>
   <td>21/tcp
   </td>
   <td>open
   </td>
   <td>ftp
   </td>
   <td>Microsoft ftpd
   </td>
  </tr>
  <tr>
   <td>80/tcp
   </td>
   <td>open
   </td>
   <td>http
   </td>
   <td>Microsoft IIS httpd 7.5
   </td>
  </tr>
  <tr>
   <td>135/tcp
   </td>
   <td>open
   </td>
   <td> msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>139/tcp
   </td>
   <td>open
   </td>
   <td>netbios-ssn
   </td>
   <td>Microsoft Windows netbios-ssn
   </td>
  </tr>
  <tr>
   <td>445/tcp
   </td>
   <td>open
   </td>
   <td>microsoft-ds
   </td>
   <td>Microsoft Windows 7 - 10 microsoft-ds (workgroup: WORKGROUP)
   </td>
  </tr>
  <tr>
   <td>3389/tcp
   </td>
   <td>open
   </td>
   <td>rtsp
   </td>
   <td>ssl/ms-wbt-server
   </td>
  </tr>
  <tr>
   <td>5985/tcp
   </td>
   <td>open
   </td>
   <td>
   </td>
   <td>Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
   </td>
  </tr>
  <tr>
   <td>47001/tcp
   </td>
   <td>open
   </td>
   <td>http
   </td>
   <td>Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
   </td>
  </tr>
  <tr>
   <td>49152/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>49153/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>49154/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>49155/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>49165/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>49166/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
</table>

<br>
<br>

**Nmap scan report for 10.0.0.123**

[Full Report Target IP: 10.0.0.123](https://docs.google.com/document/d/1DmG7kq7XZPEi4DSdOrLtOIB4Rw1quzx2UX8QTrhqMqs/edit?usp=sharing)

* Host is up (0.024s latency).
* Not shown: 996 closed tcp ports (conn-refused)
* Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

<table>
  <tr>
   <td>
<strong>Port:</strong>
   </td>
   <td><strong>State:</strong>
   </td>
   <td><strong>Service:</strong>
   </td>
   <td><strong>Version:</strong>
   </td>
  </tr>
  <tr>
   <td>22/tcp
   </td>
   <td>open
   </td>
   <td>ssh
   </td>
   <td>OpenSSH 7.6p1 Ubuntu 4 (Ubuntu Linux; protocol 2.0)
   </td>
  </tr>
  <tr>
   <td>111/tcp
   </td>
   <td>open
   </td>
   <td>rpcbind
   </td>
   <td>2-4 (RCP #100000)
   </td>
  </tr>
  <tr>
   <td>2049/tcp
   </td>
   <td>open
   </td>
   <td>nfs
   </td>
   <td>3-4 (RPC #100003)
   </td>
  </tr>
  <tr>
   <td>8089/tcp
   </td>
   <td>open
   </td>
   <td>ssl/http
   </td>
   <td>Splunkd httpd
   </td>
  </tr>
</table>

<br>
<br>

**Nmap scan report for 10.0.0.126**

[Full Report Target IP: 10.0.0.126](https://docs.google.com/document/d/1CSUhmWC-5mXrTpc7Mh5gOF_qkhHigSN6o-si4Nmr4oE/edit?usp=sharing)

* Host is up (0.10s latency).
* Not shown: 995 closed tcp ports (conn-refused)
* Service Info:  OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

<table>
  <tr>
   <td>
<strong>Port:</strong>
   </td>
   <td><strong>State:</strong>
   </td>
   <td><strong>Service:</strong>
   </td>
   <td><strong>Version:</strong>
   </td>
  </tr>
  <tr>
   <td>135/tcp
   </td>
   <td>open
   </td>
   <td> msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>139/tcp
   </td>
   <td>open
   </td>
   <td>netbios-ssn
   </td>
   <td>Microsoft Windows netbios-ssn
   </td>
  </tr>
  <tr>
   <td>445/tcp
   </td>
   <td>open
   </td>
   <td>microsoft-ds
   </td>
   <td>Microsoft Windows Server 2008 R2 - 2012 microsoft-ds
   </td>
  </tr>
  <tr>
   <td>3389/tcp
   </td>
   <td>open
   </td>
   <td>ms-wbt-server
   </td>
   <td>Microsoft Terminal Services
   </td>
  </tr>
  <tr>
   <td>5985/tcp
   </td>
   <td>open
   </td>
   <td>http
   </td>
   <td>Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
   </td>
  </tr>
  <tr>
   <td>8089/tcp
   </td>
   <td>open
   </td>
   <td>ssl/http
   </td>
   <td>Splunkd httpd
   </td>
  </tr>
  <tr>
   <td>47001/tcp
   </td>
   <td>open
   </td>
   <td>http
   </td>
   <td>Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
   </td>
  </tr>
  <tr>
   <td>49664/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td> 49665/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td> 49666/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td> 49667/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td> 49669/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>49673/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>49675/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td> 49688/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
</table>

<br>
<br>

**Nmap scan report for 10.0.0.175**

[Full Report Target IP: 10.0.0.175](https://docs.google.com/document/d/1d9143DpVtrQDVd-MzzgrbaQmcTp64PzeyqIauNhJm90/edit?usp=sharing)

* Host is up (0.026s latency).
* Not shown: 997 closed tcp ports (conn-refused)
* Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

<table>
  <tr>
   <td>
<strong>Port:</strong>
   </td>
   <td><strong>State:</strong>
   </td>
   <td><strong>Service:</strong>
   </td>
   <td><strong>Version:</strong>
   </td>
  </tr>
  <tr>
   <td>22/tcp
   </td>
   <td>open
   </td>
   <td>ssh
   </td>
   <td>OpenSSH 8.2p1 Ubuntu 4Ubuntu0.2 (Ubuntu Linux; protocol 2.0
   </td>
  </tr>
  <tr>
   <td>80/tcp
   </td>
   <td>open
   </td>
   <td>http
   </td>
   <td>Apache httpd 2.4.41 (Ubuntu)
   </td>
  </tr>
  <tr>
   <td>8089/tcp
   </td>
   <td>open
   </td>
   <td>Splunkd
   </td>
   <td>httpd
   </td>
  </tr>
</table>

<br>
<br>

**Nmap scan report for 10.0.0.197**

[Full Report Target IP: 10.0.0.197](https://docs.google.com/document/d/1k2nKWm7MutmYQiwW_aAe-uyqv807U5vsN7FwY9vT0ac/edit?usp=sharing)

* Host is up (0.025s latency).
* Not shown: 995 closed tcp ports (conn-refused)
* Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

<table>
  <tr>
   <td>
<strong>Port:</strong>
   </td>
   <td><strong>State:</strong>
   </td>
   <td><strong>Service:</strong>
   </td>
   <td><strong>Version:</strong>
   </td>
  </tr>
  <tr>
   <td>135/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>139/tcp
   </td>
   <td>open
   </td>
   <td>netbios-ssn
   </td>
   <td>Microsoft Windows netbios-ssn
   </td>
  </tr>
  <tr>
   <td>445/tcp
   </td>
   <td>open
   </td>
   <td>Dcr
   </td>
   <td>Windows Server 2019 Standard Evaluation 17763 microsoft-ds
   </td>
  </tr>
  <tr>
   <td>3389/tcp
   </td>
   <td>open
   </td>
   <td>ms-wbt-server
   </td>
   <td>Microsoft Terminal Services
   </td>
  </tr>
  <tr>
   <td>8089/tcp
   </td>
   <td>open
   </td>
   <td>ssl/http
   </td>
   <td>Splunkd httpd
   </td>
  </tr>
</table>

<br>
<br>

**Nmap scan report for 10.0.0.206**

[Full Report Target IP: 10.0.0.206](https://docs.google.com/document/d/1qx-PHcWE_f2YKffttKsRHg84IzifhlFxXG99OibC0FU/edit?usp=sharing)

* Host is up (0.025s latency).
* Not shown: 995 closed tcp ports (conn-refused)
* Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

<table>
  <tr>
   <td>
<strong>Port:</strong>
   </td>
   <td><strong>State:</strong>
   </td>
   <td><strong>Service:</strong>
   </td>
   <td><strong>Version:</strong>
   </td>
  </tr>
  <tr>
   <td>135/tcp
   </td>
   <td>open
   </td>
   <td>msrpc
   </td>
   <td>Microsoft Windows RPC
   </td>
  </tr>
  <tr>
   <td>139/tcp
   </td>
   <td>open
   </td>
   <td>netbios-ssn
   </td>
   <td>Microsoft Windows netbios-ssn
   </td>
  </tr>
  <tr>
   <td>445/tcp
   </td>
   <td>open
   </td>
   <td> Dcr
   </td>
   <td>Windows Server 2019 Standard Evaluation 17763 microsoft-ds
   </td>
  </tr>
  <tr>
   <td>3389/tcp
   </td>
   <td>open
   </td>
   <td>ms-wbt-server
   </td>
   <td>Microsoft Terminal Services
   </td>
  </tr>
  <tr>
   <td>8089/tcp
   </td>
   <td>open
   </td>
   <td>ssl/http
   </td>
   <td>Splunkd httpd
   </td>
  </tr>
</table>
