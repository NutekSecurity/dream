# Network protocols

The maximum number of ports is **65,535**.

This limit applies to TCP and UDP ports, which are used to identify different services or applications running on a computer network. They are represented by 16-bit unsigned integers, meaning they can range from 0 to 65,535 (2^16 - 1).

Here's a breakdown:

* **Port 0:** Reserved and cannot be used.
* **Ports 1-1023:** Well-known ports assigned to standard services like HTTP (port 80), FTP (port 21), and SSH (port 22).
* **Ports 1024-49151:** Registered ports assigned by IANA (Internet Assigned Numbers Authority) to specific applications.
* **Ports 49152-65535:** Dynamic or private ports used by applications for temporary connections.
 