# **Ansible Role for Network Device Image Updates**

## **Overview**
Ansible role to update different network devices.
Including prechecks, main update, postcheck and rollback procedure. 

## **Official Guide and Documentations
https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus9000/sw/7-x/fundamentals/configuration/guide/b_Cisco_Nexus_9000_Series_NX-OS_Fundamentals_Configuration_Guide_7x/b_Cisco_Nexus_9000_Series_NX-OS_Fundamentals_Configuration_Guide_7x_chapter_01000.html

## **Pre Check Process

## **Main Upgrade Process
Steps:
  * check if file is already present on device
  * check if checksum is correct (skipping if checksum is empty)
  * copy file to device only if file not present or checksum incorrect
  * again verify checksum if variable is given
  * delete file if checksum wrong
