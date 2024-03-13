# Wireshark basics

ARP Overview

ARP or Address Resolution Protocol is a Layer 2 protocol that is used to connect IP Addresses with MAC Addresses. They will contain REQUEST messages and RESPONSE messages. To identify packets the message header will contain one of two operation codes:

Request (1)
Reply (2)

ARP Request

When a device wants to send a packet to another device on the same network, it will first send an ARP request to find the MAC address of the destination device. The ARP request will contain the IP address of the destination device and the MAC address of the source device.

ARP Reply

When the destination device receives the ARP request, it will send an ARP reply to the source device. The ARP reply will contain the MAC address of the destination device.

ARP Spoofing

ARP spoofing is a type of attack in which an attacker sends fake ARP messages to a network. The goal of the attack is to associate the attacker's MAC address with the IP address of another device on the network. This can be used to intercept traffic between two devices or to perform

ARP Cache

ARP cache is a table that contains the IP address and MAC address of devices on the network. When a device sends an ARP request, it will store the IP address and MAC address of the device in the ARP cache. The ARP cache is used to speed up the process of sending packets to devices on the network.

ARP Table

ARP table is a table that contains the IP address and MAC address of devices on the network. When a device sends an ARP request, it will store the IP address and MAC address of the device in the ARP table. The ARP table is used to speed up the process of sending packets to devices on the network.

ARP Poisoning

ARP poisoning is a type of attack in which an attacker sends fake ARP messages to a network. The goal of the attack is to associate the attacker's MAC address with the IP address of another device on the network. This can be used to intercept traffic between two devices or to perform

ARP Cache Poisoning

ARP cache poisoning is a type of attack in which an attacker sends fake ARP messages to a network. The goal of the attack is to associate the attacker's MAC address with the IP address of another device on the network. This can be used to intercept traffic between two devices or to perform

ARP Table Poisoning

ARP table poisoning is a type of attack in which an attacker sends fake ARP messages to a network. The goal of the attack is to associate the attacker's MAC address with the IP address of another device on the network. This can be used to intercept traffic between two devices or to perform

ICMP Overview

ICMP or Internet Control Message Protocol is used to analyze various nodes on a network. This is most commonly used with utilities like ping and traceroute.

ICMP Echo Request

An ICMP Echo Request is a message that is sent to a device to check if it is online. The device will respond with an ICMP Echo Reply.

ICMP Echo Reply

An ICMP Echo Reply is a message that is sent to a device to check if it is online. The device will respond with an ICMP Echo Reply.

ICMP Redirect

An ICMP Redirect is a message that is sent to a device to inform it that there is a better route to a destination.

ICMP Time Exceeded

An ICMP Time Exceeded is a message that is sent to a device to inform it that a packet has exceeded its time to live.

ICMP Destination Unreachable

An ICMP Destination Unreachable is a message that is sent to a device to inform it that a packet cannot be delivered to its destination.

ICMP Source Quench

An ICMP Source Quench is a message that is sent to a device to inform it that it is sending too many packets.

ICMP Parameter Problem

An ICMP Parameter Problem is a message that is sent to a device to inform it that a packet has an invalid header.

ICMP Timestamp Request

An ICMP Timestamp Request is a message that is sent to a device to request the current time.

ICMP Timestamp Reply

An ICMP Timestamp Reply is a message that is sent to a device to respond to a Timestamp Request.

ICMP Information Request

An ICMP Information Request is a message that is sent to a device to request information about the device.

ICMP Information Reply

An ICMP Information Reply is a message that is sent to a device to respond to an Information Request.

ICMP Address Mask Request

An ICMP Address Mask Request is a message that is sent to a device to request the subnet mask of the device.

ICMP Address Mask Reply

An ICMP Address Mask Reply is a message that is sent to a device to respond to an Address Mask Request.

ICMP Router Advertisement

An ICMP Router Advertisement is a message that is sent to a device to inform it that there is a router on the network.

ICMP Router Solicitation

An ICMP Router Solicitation is a message that is sent to a device to request information about the router on the network.

ICMP Router Discovery

An ICMP Router Discovery is a message that is sent to a device to request information about the router on the network.

ICMP Time Stamp

An ICMP Time Stamp is a message that is sent to a device to request the current time.

ICMP request:

Below we see packet details for a ping request packet. There are a few important things within the packet details that we can take note of first being the type and code of the packet. A type that equals 8 means that it is a request packet, if it is equal to 0 it is a reply packet. When these codes are altered or do not seem correct that is typically a sign of suspicious activity.

There are two other details within the packet that are useful to analyze: timestamp and data. The timestamp can be useful for identifying the time the ping was requested it can also be useful to identify suspicious activity in some cases. We can also look at the data string which will typically just be a random data string.

ICMP reply:

Below we see packet details for a ping reply packet. There are a few important things within the packet details that we can take note of first being the type and code of the packet. A type that equals 8 means that it is a request packet, if it is equal to 0 it is a reply packet. When these codes are altered or do not seem correct that is typically a sign of suspicious activity.

There are two other details within the packet that are useful to analyze: timestamp and data. The timestamp can be useful for identifying the time the ping was requested it can also be useful to identify suspicious activity in some cases. We can also look at the data string which will typically just be a random data string.

ICMP redirect:

Below we see packet details for an ICMP redirect packet. There are a few important things within the packet details that we can take note of first being the type and code of the packet. A type that equals 8 means that it is a request packet, if it is equal to 0 it is a reply packet. When these codes are altered or do not seem correct that is typically a sign of suspicious activity.

ICMP Reply:

Below you can see that the reply packet is very similar to the request packet. One of the main difference that distinguishes a reply packet is the code, in this case, you can see it is 0, confirming that it is a reply packet.

The same analysis techniques for Request packets apply here as well, again the main difference will be the packet type.

TCP Overview

TCP or Transmission Control Protocol handles the delivery of packets including sequencing and errors.

When analyzing TCP packets, Wireshark can be very helpful and color code the packets in order of danger level. If you can't remember the color code go back to Task 3 and refresh on how Wireshark uses colors to match packets.

TCP can give useful insight into a network when analyzing however it can also be hard to analyze due to the number of packets it sends. This is where you may need to use other tools like RSA NetWitness and NetworkMiner to filter out and further analyze the captures.

A common thing that you will see when analyzing TCP packets is known as the TCP handshake, which you should already be familiar with. It includes a series of packets: syn, synack, ack; That allows devices to establish a connection.

TCP SYN

The TCP SYN packet is the first packet in the TCP handshake. It is used to initiate a connection between two devices.

TCP SYN-ACK

The TCP SYN-ACK packet is the second packet in the TCP handshake. It is used to acknowledge the receipt of the TCP SYN packet.

TCP ACK

The TCP ACK packet is the third packet in the TCP handshake. It is used to acknowledge the receipt of the TCP SYN-ACK packet.

TCP RST

The TCP RST packet is used to reset a connection between two devices.

TCP FIN

The TCP FIN packet is used to close a connection between two devices.

TCP PSH

The TCP PSH packet is used to push data to a device.

TCP URG

The TCP URG packet is used to send urgent data to a device.

TCP Window Size

The TCP Window Size is used to control the flow of data between two devices.

TCP Checksum

The TCP Checksum is used to verify the integrity of the TCP header.

TCP Options

The TCP Options are used to control the behavior of the TCP protocol.

TCP Flags

The TCP Flags are used to control the behavior of the TCP protocol.

TCP Sequence Number

The TCP Sequence Number is used to keep track of the order of packets.

TCP Acknowledgment Number

The TCP Acknowledgment Number is used to acknowledge the receipt of packets.

TCP Header Length

The TCP Header Length is used to control the size of the TCP header.

TCP Urgent Pointer

The TCP Urgent Pointer is used to send urgent data to a device.

DNS or Domain Name Service protocol is used to resolves names with IP addresses.

There are a couple of things outlined below that you should keep in the back of your mind when analyzing DNS packets.

- Query-Response
- DNS-Servers Only
- UDP

If anyone of these is out of place then the packets should be looked at further and should be considered suspicious.

Instantly looking at the packets we can see what they are querying, this can be useful when you have many packets and need to identify suspicious or unusual traffic quickly.

DNS Query

The DNS Query packet is used to request the IP address of a domain name.

Looking at the below query we really have two bits of information that we can use to analyze the packet. The first bit of information we can look at is where the query is originating from, in this case, it is UDP 53 which means that this packet passes that check, if it was TCP 53 then it should be considered suspicious traffic and needs to analyzed further. We can also look at what it is querying as well, this can be useful with other information to build a story of what happened.

DNS Response

The DNS Response packet is used to respond to a DNS Query packet.

Below we see a response packet, it is similar to the query packet, but it includes an answer as well which can be used to verify the query.

DNS Query and Response

The DNS Query and Response packet is used to request the IP address of a domain name and respond to the request.

HTTP or Hypertext Transfer Protocol is a commonly used port for the world wide web and used by some websites, however, its encrypted counterpart: HTTPS is more common which we will discuss in the next text. HTTP is used to send GET and POST requests to a web server in order to receive things like webpages. Knowing how to analyze HTTP can be helpful to quickly spot things like SQLi, Web Shells, and other web-related attack vectors.

HTTP is one of the most straight forward protocols for packet analysis, the protocol is straight to the point and does not include any handshakes or prerequisites before communication.

Above we can see a sample HTTP packet, looking at an HTTP packet we can easily gather information since the data stream is not encrypted like the HTTP counterpart HTTPS. Some of the important information we can gather from the packet is the Request URI, File Data, Server.

Now that we understand the basic structure of an HTTP packet we can move on to looking at a sample HTTP packet capture to get hands-on with the packets.

From this packet we can identify some very important information like the host, user-agent, requested URI, and response.

HTTPS or Hypertext Transfer Protocol Secure is the encrypted counterpart to HTTP. It is used to send GET and POST requests to a web server in order to receive things like webpages. Knowing how to analyze HTTPS can be helpful to quickly spot things like SQLi, Web Shells, and other web-related attack vectors.

HTTPS or Hypertext Transfer Protocol Secure can be one of the most annoying protocols to understand from a packet analysis perspective and can be confusing to understand the steps needed to take in order to analyze HTTPS packets.

The first thing to understand is that HTTPS is encrypted, this means that the data stream is not visible to the naked eye and will need to be decrypted in order to analyze the packets.

The first step to decrypting HTTPS packets is to obtain the private key of the server that you are analyzing. This can be done by asking the server owner for the private key or by using a tool like RSA NetWitness to decrypt the packets.

Once you have the private key you can use RSA NetWitness to decrypt the packets and analyze them.

From this packet we can identify some very important information like the host, user-agent, requested URI, and response.

HTTPS Traffic Overview

Before sending encrypted information the client and server need to agree upon various steps in order to make a secure tunnel.

- Client and server agree on a protocol version
- Client and server select a cryptographic algorithm
- The client and server can authenticate to each other; this step is optional
- Creates a secure tunnel with a public key

We can begin analyzing HTTPS traffic by looking at packets for the handshake between the client and the server. Below is a Client Hello packet showing the SSLv2 Record Layer, Handshake Type, and SSL Version.

Below is the Server Hello packet sending similar information as the Client Hello packet however this time it includes session details and SSL certificate information

Below is the Client Key Exchange packet, this packet is used to send the pre-master secret to the server.

Below is the Client Key Exchange packet, this part of the handshake will determine the public key to use to encrypt further messages between the Client and Server.

In the next packet, the server will confirm the public key and create the secure tunnel, all traffic after this point will be encrypted based on the agreed-upon specifications listed above.

