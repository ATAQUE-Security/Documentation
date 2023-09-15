<p style="text-align: right">
09/13/23</p>

<img src="../assets/ring.png" width="250">

## **ATAQUE Penetration Test**

## **Target: 10.0.0.175**

**IP Address:** 10.0.0.175

**Date, Time initial contact** 12 SEP 2023 1500hrs

**Hostname:**

**Purpose/Description:**

**Location:** AWS Cloud Services

**Owner/Responsible Party:** SimCorp

**Network Segment/Subnet:** 10.0.0.0/24

**Operating System:** Microsoft Windows

**Open Ports and Services:**

- *List the open ports along with the associated services (e.g., Port 22 - SSH, Port 80 - HTTP)*

<br>

Nmap scan report for 10.0.0.175

- Host is up (0.026s latency).
- Not shown: 997 closed tcp ports (conn-refused)
- Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

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

## **Vulnerability Explanation:** (22/tcp  - ssh)

- OpenSSH (7.6p1 Ubuntu 4 (Ubuntu Linux; protocol 2.0) is a common service for remote administration. If not properly secured and/or on older versions of the software might make it more vulnerable to attackers.

<br>

## **Vulnerability Fix:**

- Disable root login.
- Regularly update OpenSSH to the latest version.
- Possibly implement fail2ban to block IP addresses that show malicious signs.
- Ensure the use of strong, unique passwords or, even better, use key-based authentication.

<br>

## **Severity**: High

<br>
<br>

## **Vulnerability Explanation:** (80/tcp  - info)

- This is an Apache server running on the default HTTP port. If not properly secured, it could be easily susceptible to attacks.

<br>

## **Vulnerability Fix:**

- Regularly update to the latest version.
- Implement firewall rules to restrict access.
- Limit access to required authorized users.

<br>

## **Severity**: High

<br>
<br>

## **Vulnerability Explanation:** (8089/tcp  - info)

- This is running Splunk, a software platform used in threat scanning, hunting and alerts. If not properly secured with authentication and authorization, access may be easily available. Accessible files such as robots.txt could hold important information. This scan shows Splunk is using a default certificate, this could easily be bypassed.

<br>

## **Vulnerability Fix:**

- Splunk properly configured for logging, capturing, alerting, etc..
- Regularly update to the latest version.
- Limit access to trusted users only.

<br>

## **Severity**: High

<br>

### Additional Notes

- *Add any supplementary information, observations, or context that may be relevant to this IP address*

<br>

### **Resources**

- [Nmap](https://nmap.org/)
- [Hydra](https://www.kali.org/tools/hydra/)
- [HackTricks](https://book.hacktricks.xyz/welcome/readme)

<br>

### Revisions

- Created 9/11/2023 1720hrs. David Siebert
- Updated 9/12/2023 Raphael Chookagian
- Updated 9/13/2023 Raphael Chookagian
