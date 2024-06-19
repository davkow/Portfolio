# How to: Install BIG-IP Next Central Manager on VMWare ESXi

## Overview

Procedures to download and install BIG-IP Next Central Manager from a VMWare ESXi Host Client.

## Prerequisites
- Active My F5 account
- VMware ESXi Host Client installed on a system with:
  - 8 VCPUs 
  - 16GB of RAM
  - 350GB of disk space
- Network resources:
  - IP Address, subnet, and hostname
  - NTP Server
  - DNS Server
  - Gateway Router


## Summary

- [Download BIG-IP Next Central Manager](#download-big-ip-next-central-manager)
- [Install BIG-IP Next Central Manager](#install-big-ip-next-central-manager)
- [Launch console and change password](#launch-console-and-change-password)
- [Run the setup script](#run-the-setup-script)
- [Log in to BIG-IP Central Manager and create a new password](#log-in-to-big-ip-central-manager-and-create-a-new-password)


## Procedures

## Download BIG-IP Next Central Manager

1. Sign in to [MyF5](https://account.f5.com/myf5).
2. From the top menu, click **Resources**, and then click **Downloads**.
3. Read the end user license agreement and program terms and then select the checkox to agree to the terms.
4. Click **Next**.
5. From the **Group** list, select **BIG-IP Next**. 
6. From the **Product Line** list, select **Central Manager**. 
7. From the **Product Version** list, select a version number.
8. Select a **product container** and **download file**.
9. From the **Download locations**, select the location closest to you.
10. Click **Download**.

## Install BIG-IP Next Central Manager

1. Log in to VMWare ESXi Host Client.
2. In the left pane, click **Virtual Machines**.
3. In the right pane, **Create / Register VM**. 
4. From the right page, for the **Select creation type**, select **Deploy a virtual machine from an OVF or OVA file**, and then click **Next**.
5. For **Enter a name for the virtual machine**, type the name of your VM, and then select the downloaded OVA file.
6. Select a storage type and datastore. Click **Next**.
7. For the Deployment options: 
   - From the **Network mappings** list, select one based on your system (example: **VM Network**)
   - For **Disk provisioning**, select **Thin** or **Thick**.
   - For **Power on automatically**, retain the default (check box selected).
8. Review your selections and click **Finish**.

   **Note**: For a VM in a lab environment, you can set both the CPU and Memory **Reservation** to the default (**None**). You may need to change these two settings for a production environment. Power down the VM before making changes and make sure you click **SAVE** after changing the settings.

## Launch console and change password

1. After the BIG-IP Central Manager installation is complete, log in to VMWare ESXi Host Client.
2. In the left pane, select the new VM.
3. In the right pane, click **Console**, and select a console. **Example:** **Open browser console**.<br>
   The console window opens.
4. For both the **central-manager login** and **Password**, type **admin**. 
   You are required to change your password… displays.
5. Change your password. Type:
   - **Current password**
   - **New password**
   - **Retype new password**<br>
     The Welcome information displays.

## Run the setup script

1. At the **$** prompt, type **setup**.<br>
   Welcome... and instructions display.

2. Type inputs.

   Example values are shown within parentheses. If there is a default value, it will be shown within square brackets and will automatically be used if no value is entered.

   **Network with DHCP**
   - Hostname (example.com):<br>
     [‘10.145.77.192’] found on the management interface.
   - Do you want to configure a static IP address (N/y) [N]:
   - Primary NTP server address (0.pool.ntp.org) (optional):
   - Alternate NTP server address (1.pool.ntp.org (optional):

   **Network with a management IP address (No DHCP)**
   - Hostname (e.g. example.com):
   - Management IP Address & Network Mask [192.168.1.245/24]:
   - Management Network Default Gateway [192.168.1.1]:
   - Primary DNS nameserver (e.g. 192.168.1.2):
   - Alternate DNS nameserver (e.g. 192.168.1.3) (optional):
   - Primary NTP server address (i.e 0.ubuntu.pool.ntp.org) (optional):
   - Alternate NTP server address (e.g. 1.ubuntu.pool.ntp.org (optional):
   - IPv4 network CIDR to use for service IPs [100.75.0.0/16]:
   - IPv4 network CIDR to use for pod IPs [100.76.0.0/14]:
 
     **Note:** Concerning the two inputs for service and pod IPs: the system uses the two internal IP addresses for communication between individual containers. Make sure the defaults listed do not conflict with the existing IP address space on your network. If they do, choose a different IP range for the service and pod IPs to resolve the conflict.

## Log in to BIG-IP Central Manager and create a new password 

1. From a web browser, navigate to the address previously configured: ``https://<cm-ip-address-or-hostname/>``.<br>
   The BIG-IP Next Central Manager Sign In window opens.

2. For both the **User Name** and **Password**, type ``admin``.
3. Click **Sign In**.   
4. Change your password by typing **Current Password** and **New Password**.
5. Click **Save**.
6. Log in again by typing your **User Name** and **Password**.
   
   The Welcome to BIG-IP Next Central Manager! window opens. You can now start using BIG-IP Next Central Manager.