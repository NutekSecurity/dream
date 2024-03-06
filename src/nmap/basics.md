# Nmap basics

## Host discovery

### DRY run

```bash
nmap -sL TARGETS
```

Nmap will attempt a reverse-DNS resolution on all the targets to obtain their names. Names might reveal various information to the pentester. (If you don’t want Nmap to the DNS server, you can add `-n`.)

If you want to ping a system on the same subnet, an ARP query should precede the ICMP Echo. This is called ARP ping. To perform an ARP ping, use the `-PR` option.

### Ping scan

```bash
nmap -sn TARGETS
```

only scans for live hosts

### TCP SYN scan

```bash
nmap -sS TARGETS
```

### TCP connect scan

```bash
nmap -sT TARGETS
```

### UDP scan

```bash
nmap -sU TARGETS
```

### IP protocol scan

```bash
nmap -sO TARGETS
```

### ARP scan

```bash
nmap -PR TARGETS
```

```bash
nmap -PR -sn TARGETS
```

ARP scan without port scanning

### ICMP echo scan

```bash
nmap -PE TARGETS
```

### ICMP timestamp scan

```bash
nmap -PP TARGETS
```

### ICMP netmask scan

```bash
nmap -PM TARGETS
```

### ICMP address mask scan

```bash
nmap -PO TARGETS
```

### ICMP router advertisement scan

```bash
nmap -PR TARGETS
```

### ICMP redirect scan

```bash
nmap -PR TARGETS
```

### ICMP router discovery scan

```bash
nmap -PR TARGETS
```

### ICMP information scan

```bash
nmap -PR TARGETS
```

### TCP ACK scan

```bash
nmap -sA TARGETS
```

### TCP window scan

```bash
nmap -sW TARGETS
```

### TCP Maimon scan

```bash
nmap -sM TARGETS
```

### TCP Null scan

```bash
nmap -sN TARGETS
```

### TCP Xmas scan

```bash
nmap -sX TARGETS
```

### TCP FIN scan

```bash
nmap -sF TARGETS
```

### TCP RPC scan

```bash
nmap -sR TARGETS
```

### TCP SYN/ACK scan

```bash
nmap -sY TARGETS
```

### IP IDLE scan

```bash
nmap -sI TARGETS
```

### IP IDLE scan

```bash
nmap -sI TARGETS
```

### TCP SYN ping

```bash
nmap -PS TARGETS
```

If you want Nmap to use TCP SYN ping, you can do so via the option -PS followed by the port number, range, list, or a combination of them. For example, -PS21 will target port 21, while -PS21-25 will target ports 21, 22, 23, 24, and 25. Finally -PS80,443,8080 will target the three ports 80, 443, and 8080.

### TCP ACK ping

```bash
nmap -PA TARGETS
```

By default, port 80 is used. The syntax is similar to TCP SYN ping. -PA should be followed by a port number, range, list, or a combination of them. For example, consider -PA21, -PA21-25 and -PA80,443,8080. If no port is specified, port 80 will be used.

### UDP ping

```bash
nmap -PU TARGETS
```

Nmap’s default behaviour is to use reverse-DNS online hosts. Because the hostnames can reveal a lot, this can be a helpful step. However, if you don’t want to send such DNS queries, you use -n to skip this step.

By default, Nmap will look up online hosts; however, you can use the option -R to query the DNS server even for offline hosts. If you want to use a specific DNS server, you can add the --dns-servers DNS_SERVER option.

You have learned how ARP, ICMP, TCP, and UDP can detect live hosts by completing this room. Any response from a host is an indication that it is online. Below is a quick summary of the command-line options for Nmap that we have covered.

| Scan Type                | Example Command                          |
|--------------------------|------------------------------------------|
| ARP Scan                 | sudo nmap -PR -sn MACHINE_IP/24          |
| ICMP Echo Scan           | sudo nmap -PE -sn MACHINE_IP/24          |
| ICMP Timestamp Scan      | sudo nmap -PP -sn MACHINE_IP/24          |
| ICMP Address Mask Scan   | sudo nmap -PM -sn MACHINE_IP/24          |
| TCP SYN Ping Scan        | sudo nmap -PS22,80,443 -sn MACHINE_IP/30 |
| TCP ACK Ping Scan        | sudo nmap -PA22,80,443 -sn MACHINE_IP/30 |
| UDP Ping Scan            | sudo nmap -PU53,161,162 -sn MACHINE_IP/30|

Remember to add -sn if you are only interested in host discovery without port-scanning. Omitting -sn will let Nmap default to port-scanning the live hosts.

| Option | Purpose               |
|--------|-----------------------|
| -n     | no DNS lookup         |
| -R     | reverse-DNS lookup for all hosts |
| -sn    | host discovery only   |


## masscan

### DRY run

```bash
masscan -n --rate 1000 --echo TARGETS
```


```bash
masscan -p1-65535 --rate 1000 TARGETS
```

## Nmap scripts

### List scripts

```bash
ls /usr/share/nmap/scripts
```

### Run a script

```bash
nmap --script SCRIPT TARGETS
```

### Run a category of scripts

```bash
nmap --script CATEGORY TARGETS
```

### Run a script with arguments

```bash
nmap --script SCRIPT --script-args ARGUMENTS TARGETS
```

### Run a script with a category of scripts and arguments

```bash
nmap --script CATEGORY --script-args ARGUMENTS TARGETS
```

In the same sense that an IP address specifies a host on a network among many others, a TCP port or UDP port is used to identify a network service running on that host. A server provides the network service, and it adheres to a specific network protocol. Examples include providing time, responding to DNS queries, and serving web pages. A port is usually linked to a service using that specific port number. For instance, an HTTP server would bind to TCP port 80 by default; moreover, if the HTTP server supports SSL/TLS, it would listen on TCP port 443. (TCP ports 80 and 443 are the default ports for HTTP and HTTPS; however, the webserver administrator might choose other port numbers if necessary.) Furthermore, no more than one service can listen on any TCP or UDP port (on the same IP address).

At the risk of oversimplification, we can classify ports in two states:

Open port indicates that there is some service listening on that port.
Closed port indicates that there is no service listening on that port.
However, in practical situations, we need to consider the impact of firewalls. For instance, a port might be open, but a firewall might be blocking the packets. Therefore, Nmap considers the following six states:

* Open: indicates that a service is listening on the specified port.
* Closed: indicates that no service is listening on the specified port, although the port is accessible. By accessible, we mean that it is reachable and is not blocked by a firewall or other security appliances/programs.
* Filtered: means that Nmap cannot determine if the port is open or closed because the port is not accessible. This state is usually due to a firewall preventing Nmap from reaching that port. Nmap’s packets may be blocked from reaching the port; alternatively, the responses are blocked from reaching Nmap’s host.
* Unfiltered: means that Nmap cannot determine if the port is open or closed, although the port is accessible. This state is encountered when using an ACK scan -sA.
* Open|Filtered: This means that Nmap cannot determine whether the port is open or filtered.
* Closed|Filtered: This means that Nmap cannot decide whether a port is closed or filtered.

In particular, we need to focus on the flags that Nmap can set or unset. We have highlighted the TCP flags in red. Setting a flag bit means setting its value to 1. From left to right, the TCP header flags are:

1. URG: Urgent flag indicates that the urgent pointer filed is significant. The urgent pointer indicates that the incoming data is urgent, and that a 
2. TCP segment with the URG flag set is processed immediately without consideration of having to wait on previously sent TCP segments.
3. ACK: Acknowledgement flag indicates that the acknowledgement number is significant. It is used to acknowledge the receipt of a TCP segment.
4. PSH: Push flag asking TCP to pass the data to the application promptly.
5. RST: Reset flag is used to reset the connection. Another device, such as a firewall, might send it to tear a TCP connection. This flag is also used when data is sent to a host and there is no service on the receiving end to answer.
6. SYN: Synchronize flag is used to initiate a TCP 3-way handshake and synchronize sequence numbers with the other host. The sequence number should be set randomly during TCP connection establishment.
7. FIN: The sender has no more data to send.

We are interested in learning whether the TCP port is open, not establishing a TCP connection. Hence the connection is torn as soon as its state is confirmed by sending a RST/ACK. You can choose to run TCP connect scan using -sT.

It is important to note that if you are not a privileged user (root or sudoer), a TCP connect scan is the only possible option to discover open TCP ports.

We notice that port 143 is open, so it replied with a SYN/ACK, and Nmap completed the 3-way handshake by sending an ACK. The figure below shows all the packets exchanged between our Nmap host and the target system’s port 143. The first three packets are the TCP 3-way handshake being completed. Then, the fourth packet tears it down with an RST/ACK packet.

Note that we can use -F to enable fast mode and decrease the number of scanned ports from 1000 to 100 most common ports.

It is worth mentioning that the -r option can also be added to scan the ports in consecutive order instead of random order. This option is useful when testing whether ports open in a consistent manner, for instance, when a target boots up.

Unprivileged users are limited to connect scan. However, the default scan mode is SYN scan, and it requires a privileged (root or sudoer) user to run it. SYN scan does not need to complete the TCP 3-way handshake; instead, it tears down the connection once it receives a response from the server. Because we didn’t establish a TCP connection, this decreases the chances of the scan being logged. We can select this scan type by using the -sS option. The figure below shows how the TCP SYN scan works without completing the TCP 3-way handshake.