# CDP Network Protocol

## CDP Network Protocol Overview

**CDP (Cisco Discovery Protocol)** is a proprietary Layer 2 protocol developed by Cisco that enables network devices to discover and learn information about directly connected neighbors. CDP operates on UDP port 2234, exchanging data packets called CDP announcements every 60 seconds by default. 

### Key Features:

* **Discovery:** Automatically discovers devices connected to the same LAN segment.
* **Information Exchange:** Shares information like device type, IP addresses, software versions, capabilities, and VLAN memberships.
* **Management Simplicity:** Helps network administrators map the network topology and identify connected devices for troubleshooting and configuration purposes.
* **Operating System Compatibility:** Supported on various Cisco devices, including routers, switches, and wireless access points.

### Information Transmitted in CDP Announcements:

* **Device ID:** Hostname or interface ID.
* **Management Addresses:** IP addresses and Layer 2 addresses.
* **Capabilities:** Protocol support, like IPX, DECnet, or AppleTalk.
* **Software Version:** Operating system information.
* **Platform:** Device type (router, switch, etc.).
* **PortID:** Interface information.
* **VLAN ID:** VLAN membership.
* **Native VLAN ID:** VLAN assigned to the interface.
* **Voice VLAN ID:** Voice VLAN assigned to the interface.

### Uses of CDP:

* **Network Troubleshooting:** Identifying connectivity issues, finding specific devices, and determining network topology.
* **Configuration Automation:** Discovering neighbors and automatically configuring protocols like VLAN trunking.
* **Management Optimization:** Reducing manual configuration and facilitating network visualization.

### CDP Limitations:

* **Cisco Proprietary:** Only functions on Cisco devices.
* **Layer 2 Protocol:** Limited to devices on the same network segment.
* **Security Concerns:** Potential for information leaks if not properly configured.

### Additional Notes:

* CDP can be enabled or disabled globally or on specific interfaces.
* CDP advertisements can be filtered based on the destination MAC address.
* Advanced features like CDP hold-time and CDP rate limit allow for optimizing network performance.


**References:**

* Cisco Discovery Protocol (CDP) Overview: https://www.ciscopress.com/articles/article.asp?p=3064416\u0026seqNum=6
* Cisco Discovery Protocol Configuration Guide: https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/iproute_bgp/configuration/15-sy/irg_bgp_15-sy-book/bgp-cdp.html
* CDP Commands: https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/iproute_bgp/configuration/15-sy/irg_bgp_15-sy-book/irg-bgp-cdp-commands.html

I hope this information is helpful! Please let me know if you have any other questions.

