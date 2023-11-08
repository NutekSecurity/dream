# IPv4

GitHub Copilot: IPv4, or Internet Protocol version 4, is the fourth version of the Internet Protocol (IP). It is one of the core protocols of standards-based internetworking methods on the Internet and was the first version deployed for production in ARPANET in 1983. It still routes most Internet traffic today, despite the ongoing deployment of a successor protocol, IPv6.

IPv4 uses 32-bit addresses which limits the address space to 4294967296 (2^32) possible unique addresses. However, many are reserved for special purposes such as private networks (~18 million addresses) or multicast addresses (~270 million addresses). This reduces the number of addresses that can be allocated as public Internet addresses.

IPv4 addresses are typically represented in dot-decimal notation, with four numbers separated by periods, each ranging from 0 to 255, for example, `192.168.0.1`.

Here are some special types of IPv4 addresses:

1. **Private Addresses**: These are reserved for private networks and are not routable on the public Internet. Examples include `192.168.0.1`, `10.0.0.1`, `172.16.0.1`.

2. **Loopback Address**: The address `127.0.0.1` is reserved for loopback. This means that it is used by the host computer to send a message back to itself for testing network software.

3. **Broadcast Address**: This is an address that allows information to be sent to all machines on a given subnet rather than a specific machine. The broadcast address of any IP address can be obtained by taking the bit complement of the subnet mask, and then performing a bitwise OR operation with the IP address itself. For example, for the IP address `192.168.0.1` with a subnet mask of `255.255.255.0`, the broadcast address would be `192.168.0.255`.

4. **Multicast Addresses**: These are used to send a single packet to a group of hosts. IPv4 multicast addresses are defined by the leading address bits of `1110`, originating from the classful network design of the early Internet when this group of addresses was designated as Class D. The CIDR notation for this group is `224.0.0.0/4`. The group includes the addresses from `224.0.0.0` to `239.255.255.255`.

Understanding IPv4 addressing is fundamental to managing and troubleshooting network activities.

IPv4 (Internet Protocol version 4) is the fourth revision of the Internet Protocol and one of the most widely used addressing schemes for the Internet. It uses a 32-bit address format, typically expressed as four sets of decimal numbers separated by periods (e.g., 192.168.1.1). Each set of numbers, known as an octet, can have a value between 0 and 255. Here are some examples of IPv4 addresses:

1. **192.168.0.1**: This is a commonly used private IP address, often assigned to a router or a local device in a home or small business network. It's part of the reserved private IP address range.

2. **10.0.0.1**: Another private IP address, often used as the default gateway for many home and business networks. It falls within the private IP address space.

3. **172.16.0.1**: This is also a private IP address, often used in larger networks. It's within the private IP address range reserved for internal use.

4. **203.0.113.12**: An example of a public IPv4 address. This address could be assigned to a web server or any device accessible from the internet. Public IP addresses are unique and routable on the global internet.

5. **8.8.8.8**: This is one of Google's public DNS server IP addresses. It's used for translating domain names into IP addresses, helping resolve internet domain names to their corresponding IP addresses.

6. **216.58.215.46**: This IP address corresponds to Google's main website. When you type "www.google.com" into your web browser, it's resolved to this IP address, allowing your browser to connect to Google's servers.

7. **198.51.100.1**: An example of an address reserved for documentation and examples. It's part of the "Test-Net" range designated in RFC 5737.

8. **127.0.0.1**: This is the loopback address, often referred to as "localhost." It's used to establish network connections with the local host (the device itself). If you ping 127.0.0.1, you're essentially testing your own network stack.

9. **169.254.0.1**: This is an Automatic Private IP Address (APIPA). It's assigned to a device when it can't obtain an IP address from a DHCP server. It's typically used for self-assigned IP addresses in local networks.

10. **0.0.0.0**: This is a special IP address used to represent the default route (gateway) or an invalid/uninitialized address in some contexts. It's not typically assigned to devices.

These examples illustrate the diversity of IPv4 addresses, which are used for various purposes, from private network addressing to public internet-facing services. IPv4, while still widely used, has limitations due to address exhaustion, leading to the development and adoption of IPv6, which provides a much larger address space.

IPv4 (Internet Protocol version 4) is the fourth version of the Internet Protocol (IP). It is the most widely used version of IP today, and it is used to address and route devices on the Internet.

IPv4 addresses are 32-bit numbers that are typically represented in dotted quad format. The dotted quad format consists of four octets, which are 8-bit numbers. The octets are separated by periods.

Here are some examples of IPv4 addresses:

* 192.168.1.1
* 10.0.0.1
* 172.16.0.1
* 8.8.8.8 (Google Public DNS)
* 1.1.1.1 (Cloudflare DNS)

IPv4 addresses are divided into different classes, depending on the first octet of the address. The classes are as follows:

* Class A: 0.0.0.0 - 127.255.255.255
* Class B: 128.0.0.0 - 191.255.255.255
* Class C: 192.0.0.0 - 223.255.255.255

Class A addresses are typically used for large networks, such as the backbone of the Internet. Class B addresses are typically used for medium-sized networks, such as corporate networks. Class C addresses are typically used for small networks, such as home networks.

IPv4 addresses are also divided into different subnets. Subnetting allows you to divide a large network into smaller networks. Subnets are created by using a subnet mask. The subnet mask is a 32-bit number that tells the router which bits of the IP address are used for the network prefix and which bits are used for the host address.

Here is an example of subnetting:

```
Network address: 192.168.1.0
Subnet mask: 255.255.255.0
Subnet: 192.168.1.0/24
```

This subnet contains 256 host addresses, from 192.168.1.1 to 192.168.1.254.

IPv4 is a complex topic, but this is a brief overview of the basics. I hope this is helpful!