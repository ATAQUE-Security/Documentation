<img src="./assets/ring.png" width="350">

# Attack Standard Operating Procedure (SOP)

## Purpose

Purpose of this SOP is to outline the process of scanning, identifying, classifying, exploiting, and gaining access and control of target(s) in a cloud computing infrastructure.

## Scope

To establish a standardized and reliable method for performing network and system attack procedures that can be implemented in any client's cloud computing infrastructure.

## Responsibilities

* **Red Team**: Responsible for scanning, identifying, classifying, exploiting, and gaining access and control

## Prerequisites

**Atack machine**:

* Ensure Kali VM (ParrotOS/etc.) attack machine is up and running and up to date with most current updates and patches.
* Implement proper SOP for attacks

**Scanning**:

* Nmap, impacket, etc..

**Reporting**:

* Ensure that all procedures, attacks, and data is collected and reported per report standards.

## Procedure

**Identification**:

* Monitor for automated alerts from the SIEM system, especially Splunk, CloudWatch, and Elastic Stack.
* Review manual reports from users or IT staff.
* Monitor for specific attack TTPs, especially those that incorporate unfamiliar Python scripts.

**Classification**:

* Classify the incident based on its severity and impact.
* Determine the appropriate response based on the classification and type of attack.

**Incident Investigation**:

* Conduct an investigation to determine the cause of the incident.
* Identify potential improvements to prevent similar incidents in the future.

**Persistence**:

* Take actions to persist command and control

**Incident Review**:

* Conduct a review to learn from the incident and improve future responses.
* Implement action items to improve the security posture of the organization.

## References

## Definitions

## Revision History

* 09/11/2023 Raphael Chookagian
