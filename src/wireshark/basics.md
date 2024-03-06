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

