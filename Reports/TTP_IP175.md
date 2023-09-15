<p style="text-align: right">
09/13/23</p>

<br>

<img src="../assets/ring.png" width="250">

## **ATAQUE Penetration Test**

[Google Docs TTP Report](https://docs.google.com/document/d/1d9143DpVtrQDVd-MzzgrbaQmcTp64PzeyqIauNhJm90/edit?usp=sharing)

<br>

## **Target: 10.0.0.175**

<br>

**Introduction**

The penetration test report for SimCorp contains all efforts that were conducted as part of an authorized and contracted penetration test of SimCorp and SimCorp networks and systems.

<br>

**Objective**

The objective of this assessment is to perform an internal penetration test against the SimCorp network. ATAQUE Security is tasked with the testing, auditing and reporting of this penetration test. The team has been given guidelines and parameters for this given test. All testing, auditing and reporting will be only on given parameters.

* Perform enumeration and exploitation against a target system within the context of a pentest

<br>

**High-Level Summary**

ATAQUE Security was tasked with performing an internal penetration test against the target. Overall objective was to evaluate the network, identify systems, and exploit flaws while reporting the findings back to Offensive Security.

<br>

## **Resources**

* [Nmap](https://nmap.org/)
* [Hydra](https://www.kali.org/tools/hydra/)
* [HackTricks](https://book.hacktricks.xyz/welcome/readme)

<br>

## **Enumeration**

Nmap scan:

Nmap scan report for 10.0.0.175

* Host is up (0.026s latency).
* Not shown: 997 closed tcp ports (conn-refused)
* Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

<br>

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

**Vulnerability Explanation:** (22/tcp  - ssh):

* OpenSSH (7.6p1 Ubuntu 4 (Ubuntu Linux; protocol 2.0) is a common service for remote administration. If not properly secured and/or on older versions of the software might make it more vulnerable to attackers.

**Vulnerability Fix:**

* Disable root login.
* Regularly update OpenSSH to the latest version.
* Possibly implement fail2ban to block IP addresses that show malicious signs.
* Ensure the use of strong, unique passwords or, even better, use key-based authentication.

**Severity**: High

**Tests:**

Using Searchsploit to find possible known exploits we can utilize.

![alt_text](images/image1.png "image_tooltip")

Using Hydra to run a brute force attack on the target. This command is using “root” as the username and the “rockyou.txt” password list to iterate through to try the passwords.

*hydra -l root -P /usr/share/wordlists/rockyou.txt 10.0.0.175 ssh*

![alt_text](images/image2.png "image_tooltip")

<br>

**Vulnerability Explanation:** (80/tcp  - info):

* This is an Apache server running on the default HTTP port. If not properly secured, it could be easily susceptible to attacks.

**Vulnerability Fix:**

* Regularly update to the latest version.
* Implement firewall rules to restrict access.
* Limit access to required authorized users.

**Severity**: High

**Tests:**

Checked http://&lt;localhost>:80 to see what the webpage/server was about.

![alt_text](images/image3.png "image_tooltip")

Used curl to bring the site data/html to investigate.

![alt_text](images/image4.png "image_tooltip")

Reviewing and investigating all images and links from the server on localhost for target IP.

![alt_text](images/image5.png "image_tooltip")

![alt_text](images/image6.png "image_tooltip")

![alt_text](images/image7.png "image_tooltip")

Directory/Path traversal following known path:

![alt_text](images/image8.png "image_tooltip")

The admin directory was accessible:

![alt_text](images/image9.png "image_tooltip")

As well as the “images” directory:

![alt_text](images/image10.png "image_tooltip")

Each image was inspected via the browser and downloaded to investigate the image metadata.

![alt_text](images/image11.png "image_tooltip")

All pdfs were investigated and downloaded for inspection.

![alt_text](images/image12.png "image_tooltip")

The passwords directory had some good information in it.

![alt_text](images/image13.png "image_tooltip")

The passwords/heroes.xml lead me to my first login credentials.

![alt_text](images/image14.png "image_tooltip")

Logged in as Neo:

![alt_text](images/image15.png "image_tooltip")

![alt_text](images/image16.png "image_tooltip")

![alt_text](images/image17.png "image_tooltip")

![alt_text](images/image18.png "image_tooltip")

![alt_text](images/image19.png "image_tooltip")

![alt_text](images/image20.png "image_tooltip")

From the passwords directory, I downloaded the wp-config.bak file to investigate and I found more information:

Database Name: bWAPP

Database User: thor

Database Password: Asgard

Database Host: localhost

![alt_text](images/image21.png "image_tooltip")

Using Hydra to ssh brute force with “thor” as the username:

![alt_text](images/image22.png "image_tooltip")

Using Medusa to ssh brute force with “thor” as the username:

![alt_text](images/image23.png "image_tooltip")

Running a scan for any wordpress directories, files, etc..

![alt_text](images/image24.png "image_tooltip")

![alt_text](images/image25.png "image_tooltip")

![alt_text](images/image26.png "image_tooltip")

![alt_text](images/image27.png "image_tooltip")

![alt_text](images/image28.png "image_tooltip")

![alt_text](images/image29.png "image_tooltip")

![alt_text](images/image30.png "image_tooltip")

<br>

**Vulnerability Explanation:** (8089/tcp  - info):

* This is running Splunk, a software platform used in threat scanning, hunting and alerts. If not properly secured with authentication and authorization, access may be easily available. Accessible files such as robots.txt could hold important information. This scan shows Splunk is using a default certificate, this could easily be bypassed.

**Vulnerability Fix:**

* Splunk properly configured for logging, capturing, alerting, etc..
* Regularly update to the latest version.
* Limit access to trusted users only.

**Severity**: High

<br>

* Created 9/12/2023 Raphael Chookagian
* Revised 9/14/2023 Raphael Chookagian
