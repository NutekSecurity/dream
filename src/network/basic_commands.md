# Basic network commands

## Table of Contents

- [Introduction](#introduction)
- [Ping](#ping)
- [Traceroute](#traceroute)
- [Netcat](#netcat)
- [Nmap](#nmap)
- [Tcpdump](#tcpdump)
- [Wireshark](#wireshark)
- [Conclusion](#conclusion)

## Introduction

When working with networks, it is important to have a good understanding of the basic network commands that can be used to troubleshoot and diagnose network issues. In this article, we will discuss some of the most commonly used network commands, including `ping`, `traceroute`, `netcat`, `nmap`, `tcpdump`, and `wireshark`.

## Ping

The `ping` command is used to test the reachability of a host on an IP network. It sends ICMP echo request packets to the target host and waits for ICMP echo reply packets. The basic syntax for `ping` is:

```bash
ping host
```

Here are some examples of how `ping` can be used:

### Basic usage

You can use `ping` to test the reachability of a host on the network. For example, to test the reachability of a host with the IP address `

```bash
ping
```

### Specifying the number of packets

You can use the `-c` option to specify the number of packets to send. For example, to send 5 packets to a host, you can use the following command:

```bash
ping -c 5 host
```

### Specifying the packet size

You can use the `-s` option to specify the size of the packets to send. For example, to send packets of size 100 bytes to a host, you can use the following command:

```bash
ping -s 100 host
```

## Traceroute

The `traceroute` command is used to trace the route that packets take to reach a target host. It sends ICMP echo request packets with increasing TTL (time to live) values and listens for ICMP time exceeded messages from intermediate routers. The basic syntax for `traceroute` is:

```bash
traceroute host
```

Here are some examples of how `traceroute` can be used:

### Basic usage

You can use `traceroute` to trace the route that packets take to reach a target host. For example, to trace the route to a host with the IP address `

```bash
traceroute
```

### Specifying the maximum number of hops

You can use the `-m` option to specify the maximum number of hops to trace. For example, to trace the route to a host with a maximum of 30 hops, you can use the following command:

```bash
traceroute -m 30 host
```

### Specifying the initial TTL

You can use the `-f` option to specify the initial TTL value. For example, to start tracing with an initial TTL of 5, you can use the following command:

```bash
traceroute -f 5 host
```

## Netcat

Netcat can be used to read and write data across network connections using the TCP/IP protocol. It can be used for a variety of purposes, such as:

- Port scanning
- Transferring files
- Chatting
- Port redirection
- Port listening
- Port forwarding
- Banner grabbing
- Port knocking
- Backdoor

The basic syntax for netcat is:

```bash
nc [options] host port
```

Here are some examples of how netcat can be used:

### Chatting

You can use netcat to chat with another user on the same network. For example, to chat with a user on the same network, you can use the following command:

```bash
nc -l -p 1234
```

This will start netcat in listening mode on port 1234. Then, the other user can connect to your machine using the following command:

```bash
nc host 1234
```

### Transferring files

You can use netcat to transfer files between two machines. For example, to send a file from one machine to another, you can use the following command on the receiving machine:

```bash
nc -l -p 1234 > file
```

This will start netcat in listening mode on port 1234 and save the incoming data to a file called "file". Then, on the sending machine, you can use the following command to send the file:

```bash
nc host 1234 < file
```

### Port scanning

You can use netcat to scan for open ports on a remote machine. For example, to scan for open ports on a remote machine, you can use the following command:

```bash
nc -z host port
```

## Nmap

The `nmap` command is used to discover hosts and services on a computer network. It is a powerful tool that can be used for network inventory, managing service upgrade schedules, and monitoring host or service uptime. The basic syntax for `nmap` is:

```bash
nmap [options] target
```

Here are some examples of how `nmap` can be used:

### Basic usage

You can use `nmap` to scan a target host for open ports. For example, to scan a host with the IP address `

```bash
nmap
```

### Specifying the scan type

You can use the `-s` option to specify the type of scan to perform. For example, to perform a TCP SYN scan on a host, you can use the following command:

```bash
nmap -sS host
```

### Specifying the port range

You can use the `-p` option to specify the range of ports to scan. For example, to scan ports 1-100 on a host, you can use the following command:

```bash
nmap -p 1-100 host
```

## Tcpdump

The `tcpdump` command is used to capture and analyze network traffic. It can be used to capture packets on a network interface and display them in real time, or save them to a file for later analysis. The basic syntax for `tcpdump` is:

```bash
tcpdump [options] [expression]
```

Here are some examples of how `tcpdump` can be used:

### Basic usage

You can use `tcpdump` to capture packets on a network interface. For example, to capture packets on the `eth0` interface, you can use the following command:

```bash
tcpdump -i eth0
```

### Specifying the number of packets to capture

You can use the `-c` option to specify the number of packets to capture. For example, to capture 100 packets on the `eth0` interface, you can use the following command:

```bash
tcpdump -c 100 -i eth0
```

### Specifying a capture filter

You can use the `expression` argument to specify a capture filter. For example, to capture only TCP traffic on the `eth0` interface, you can use the following command:

```bash
tcpdump tcp -i eth0
```

## Wireshark

Wireshark is a powerful network protocol analyzer that can be used to capture and interactively browse the traffic running on a computer network. It can be used to inspect hundreds of protocols and media types, and can be used to troubleshoot network problems, examine security problems, debug protocol implementations, and learn network protocol internals. The basic syntax for `wireshark` is:

```bash
wireshark [options] [file]
```

Here are some examples of how `wireshark` can be used:

### Basic usage

You can use `wireshark` to capture and analyze network traffic. For example, to capture packets on the `eth0` interface, you can use the following command:

```bash
wireshark -i eth0
```

### Opening a capture file

You can use the `file` argument to open a capture file for analysis. For example, to open a capture file called `capture.pcap`, you can use the following command:

```bash
wireshark capture.pcap
```

### Specifying a display filter

You can use the `-Y` option to specify a display filter. For example, to display only TCP traffic in a capture file, you can use the following command:

```bash
wireshark -Y tcp capture.pcap
```

## Conclusion


In this article, we have discussed some of the most commonly used network commands, including `ping`, `traceroute`, `netcat`, `nmap`, `tcpdump`, and `wireshark`. These commands can be used to troubleshoot and diagnose network issues, and are essential tools for anyone working with computer networks. By understanding how to use these commands, you can gain valuable insight into the behavior of your network and quickly identify and resolve network problems.
