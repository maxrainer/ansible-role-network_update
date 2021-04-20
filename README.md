# **Ansible Role for Network Device Image Updates**

## **Overview**
Ansible role to update different network devices.
Including prechecks, main update, postcheck and rollback procedure. 
Executes and compares a given "show" command before and after update process.
Verifies the image checksum before changing boot variables.
## **currently supported Platforms**
  * Cisco NXOS
## **Pre Check Process**
Steps: 
  * pull kickstart information (image and OS release string) from device 
  * execute reference check (cli_parse module used) and store result
## **Main Upgrade Process**
Steps:
  * check if file is already present on device
  * check if checksum is correct (skipping if checksum is empty)
  * copy file to device only if file not present or checksum incorrect
  * again verify checksum if variable is given
  * delete file if checksum wrong

## **Post Check Process**
only reached if upgrade process succeeded
Steps:
  * execute reference check again
  * compare reference check results (pre & post update)

## **Rollback Process**
only executed if post check fails
Steps: 
  * install previous version detected
  * check kickstart version against version before update process started
## **open caveats**
  * check diskspace available
## **Platform specific information**
* NXOS: 
  * Ansible module used for update process: 
    https://docs.ansible.com/ansible/2.10/collections/cisco/nxos/nxos_install_os_module.html#ansible-collections-cisco-nxos-nxos-install-os-module
## **Official Guides and Documentations**
* official Cisco NXOS 9k upgrade guide:
https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus9000/sw/7-x/fundamentals/configuration/guide/b_Cisco_Nexus_9000_Series_NX-OS_Fundamentals_Configuration_Guide_7x/b_Cisco_Nexus_9000_Series_NX-OS_Fundamentals_Configuration_Guide_7x_chapter_01000.html