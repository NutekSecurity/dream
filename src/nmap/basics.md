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

UDP is a connectionless protocol, and hence it does not require any handshake for connection establishment. We cannot guarantee that a service listening on a UDP port would respond to our packets. However, if a UDP packet is sent to a closed port, an ICMP port unreachable error (type 3, code 3) is returned. You can select UDP scan using the -sU option; moreover, you can combine it with another TCP scan.

However, as shown in the figure below, we expect to get an ICMP packet of type 3, destination unreachable, and code 3, port unreachable. In other words, the UDP ports that don’t generate any response are the ones that Nmap will state as open.

nmap -sU -F -v 10.10.160.249 # UDP scan with verbose output and scanning the 100 most common ports

You can control the scan timing using -T<0-5>. -T0 is the slowest (paranoid), while -T5 is the fastest. According to Nmap manual page, there are six templates:

- paranoid (0)
- sneaky (1)
- polite (2)
- normal (3)
- aggressive (4)
- insane (5)

To avoid IDS alerts, you might consider -T0 or -T1. For instance, -T0 scans one port at a time and waits 5 minutes between sending each probe, so you can guess how long scanning one target would take to finish. If you don’t specify any timing, Nmap uses normal -T3. Note that -T5 is the most aggressive in terms of speed; however, this can affect the accuracy of the scan results due to the increased likelihood of packet loss. Note that -T4 is often used during CTFs and when learning to scan on practice targets, whereas -T1 is often used during real engagements where stealth is more important.

Alternatively, you can choose to control the packet rate using --min-rate <number> and --max-rate <number>. For example, --max-rate 10 or --max-rate=10 ensures that your scanner is not sending more than ten packets per second.

Moreover, you can control probing parallelization using --min-parallelism <numprobes> and --max-parallelism <numprobes>. Nmap probes the targets to discover which hosts are live and which ports are open; probing parallelization specifies the number of such probes that can be run in parallel. For instance, --min-parallelism=512 pushes Nmap to maintain at least 512 probes in parallel; these 512 probes are related to host discovery and open ports.

This room covered three types of scans.

| Port Scan Type   | Example Command           |
|------------------|---------------------------|
| TCP Connect Scan | nmap -sT MACHINE_IP       |
| TCP SYN Scan     | sudo nmap -sS MACHINE_IP  |
| UDP Scan         | sudo nmap -sU MACHINE_IP  |

These scan types should get you started discovering running TCP and UDP services on a target host.

| Option               | Purpose                             |
|----------------------|-------------------------------------|
| -p-                  | all ports                           |
| -p1-1023             | scan ports 1 to 1023                |
| -F                   | 100 most common ports               |
| -r                   | scan ports in consecutive order     |
| -T<0-5>              | -T0 being the slowest and T5 the fastest |
| --max-rate 50        | rate <= 50 packets/sec              |
| --min-rate 15        | rate >= 15 packets/sec              |
| --min-parallelism 100| at least 100 probes in parallel     |

We will cover the following types of port scans:

- Null Scan
- FIN Scan
- Xmas Scan
- Maimon Scan
- ACK Scan
- Window Scan
- Custom Scan

Moreover, we will cover the following:

- Spoofing IP
- Spoofing MAC
- Decoy Scan
- Fragmented Packets
- Idle/Zombie Scan

The null scan does not set any flag; all six flag bits are set to zero. You can choose this scan using the -sN option. A TCP packet with no flags set will not trigger any response when it reaches an open port, as shown in the figure below. Therefore, from Nmap’s perspective, a lack of reply in a null scan indicates that either the port is open or a firewall is blocking the packet.

However, we expect the target server to respond with an RST packet if the port is closed. Consequently, we can use the lack of RST response to figure out the ports that are not closed: open or filtered.

FIN Scan
The FIN scan sends a TCP packet with the FIN flag set. You can choose this scan type using the -sF option. Similarly, no response will be sent if the TCP port is open. Again, Nmap cannot be sure if the port is open or if a firewall is blocking the traffic related to this TCP port.

However, the target system should respond with an RST if the port is closed. Consequently, we will be able to know which ports are closed and use this knowledge to infer the ports that are open or filtered. It's worth noting some firewalls will 'silently' drop the traffic without sending an RST.



Xmas Scan
The Xmas scan gets its name after Christmas tree lights. An Xmas scan sets the FIN, PSH, and URG flags simultaneously. You can select Xmas scan with the option -sX.

Like the Null scan and FIN scan, if an RST packet is received, it means that the port is closed. Otherwise, it will be reported as open|filtered.

The following two figures show the case when the TCP port is open and the case when the TCP port is closed.




One scenario where these three scan types can be efficient is when scanning a target behind a stateless (non-stateful) firewall. A stateless firewall will check if the incoming packet has the SYN flag set to detect a connection attempt. Using a flag combination that does not match the SYN packet makes it possible to deceive the firewall and reach the system behind it. However, a stateful firewall will practically block all such crafted packets and render this kind of scan useless.

TCP ACK Scan
Let’s start with the TCP ACK scan. As the name implies, an ACK scan will send a TCP packet with the ACK flag set. Use the -sA option to choose this scan. As we show in the figure below, the target would respond to the ACK with RST regardless of the state of the port. This behaviour happens because a TCP packet with the ACK flag set should be sent only in response to a received TCP packet to acknowledge the receipt of some data, unlike our case. Hence, this scan won’t tell us whether the target port is open in a simple setup.


This kind of scan would be helpful if there is a firewall in front of the target. Consequently, based on which ACK packets resulted in responses, you will learn which ports were not blocked by the firewall. In other words, this type of scan is more suitable to discover firewall rule sets and configuration.

After setting up the target VM 10.10.110.67 with a firewall, we repeated the ACK scan. This time, we received some interesting results. As seen in the console output below, we have three ports that aren't being blocked by the firewall. This result indicates that the firewall is blocking all other ports except for these three ports.

Window Scan
Another similar scan is the TCP window scan. The TCP window scan is almost the same as the ACK scan; however, it examines the TCP Window field of the RST packets returned. On specific systems, this can reveal that the port is open. You can select this scan type with the option -sW. As shown in the figure below, we expect to get an RST packet in reply to our “uninvited” ACK packets, regardless of whether the port is open or closed.



Similarly, launching a TCP window scan against a Linux system with no firewall will not provide much information. As we can see in the console output below, the results of the window scan against a Linux server with no firewall didn’t give any extra information compared to the ACK scan executed earlier.

However, as you would expect, if we repeat our TCP window scan against a server behind a firewall, we expect to get more satisfying results. In the console output shown below, the TCP window scan pointed that three ports are detected as closed. (This is in contrast with the ACK scan that labelled the same three ports as unfiltered.) Although we know that these three ports are not closed, we realize they responded differently, indicating that the firewall does not block them.

Custom

--scanflags URGACKPSHRSTSYNFIN : Customize TCP scan flags

In some network setups, you will be able to scan a target system using a spoofed IP address and even a spoofed MAC address. Such a scan is only beneficial in a situation where you can guarantee to capture the response. If you try to scan a target from some random network using a spoofed IP address, chances are you won’t have any response routed to you, and the scan results could be unreliable.

The following figure shows the attacker launching the command nmap -S SPOOFED_IP MACHINE_IP. Consequently, Nmap will craft all the packets using the provided source IP address SPOOFED_IP. The target machine will respond to the incoming packets sending the replies to the destination IP address SPOOFED_IP. For this scan to work and give accurate results, the attacker needs to monitor the network traffic to analyze the replies.



In brief, scanning with a spoofed IP address is three steps:

Attacker sends a packet with a spoofed source IP address to the target machine.
Target machine replies to the spoofed IP address as the destination.
Attacker captures the replies to figure out open ports.
In general, you expect to specify the network interface using -e and to explicitly disable ping scan -Pn. Therefore, instead of nmap -S SPOOFED_IP MACHINE_IP, you will need to issue nmap -e NET_INTERFACE -Pn -S SPOOFED_IP MACHINE_IP to tell Nmap explicitly which network interface to use and not to expect to receive a ping reply. It is worth repeating that this scan will be useless if the attacker system cannot monitor the network for responses.

When you are on the same subnet as the target machine, you would be able to spoof your MAC address as well. You can specify the source MAC address using --spoof-mac SPOOFED_MAC. This address spoofing is only possible if the attacker and the target machine are on the same Ethernet (802.3) network or same WiFi (802.11).

Spoofing only works in a minimal number of cases where certain conditions are met. Therefore, the attacker might resort to using decoys to make it more challenging to be pinpointed. The concept is simple, make the scan appear to be coming from many IP addresses so that the attacker’s IP address would be lost among them. As we see in the figure below, the scan of the target machine will appear to be coming from 3 different sources, and consequently, the replies will go the decoys as well.

You can launch a decoy scan by specifying a specific or random IP address after -D. For example, nmap -D 10.10.0.1,10.10.0.2,ME MACHINE_IP will make the scan of MACHINE_IP appear as coming from the IP addresses 10.10.0.1, 10.10.0.2, and then ME to indicate that your IP address should appear in the third order. Another example command would be nmap -D 10.10.0.1,10.10.0.2,RND,RND,ME MACHINE_IP, where the third and fourth source IP addresses are assigned randomly, while the fifth source is going to be the attacker’s IP address. In other words, each time you execute the latter command, you would expect two new random IP addresses to be the third and fourth decoy sources.

Fragmented Packets
Nmap provides the option -f to fragment packets. Once chosen, the IP data will be divided into 8 bytes or less. Adding another -f (-f -f or -ff) will split the data into 16 byte-fragments instead of 8. You can change the default value by using the --mtu; however, you should always choose a multiple of 8.

To properly understand fragmentation, we need to look at the IP header in the figure below. It might look complicated at first, but we notice that we know most of its fields. In particular, notice the source address taking 32 bits (4 bytes) on the fourth row, while the destination address is taking another 4 bytes on the fifth row. The data that we will fragment across multiple packets is highlighted in red. To aid in the reassembly on the recipient side, IP uses the identification (ID) and fragment offset, shown on the second row of the figure below.



Let’s compare running sudo nmap -sS -p80 10.20.30.144 and sudo nmap -sS -p80 -f 10.20.30.144. As you know by now, this will use stealth TCP SYN scan on port 80; however, in the second command, we are requesting Nmap to fragment the IP packets.

In the first two lines, we can see an ARP query and response. Nmap issued an ARP query because the target is on the same Ethernet. The second two lines show a TCP SYN ping and a reply. The fifth line is the beginning of the port scan; Nmap sends a TCP SYN packet to port 80. In this case, the IP header is 20 bytes, and the TCP header is 24 bytes. Note that the minimum size of the TCP header is 20 bytes.



With fragmentation requested via -f, the 24 bytes of the TCP header will be divided into multiples of 8 bytes, with the last fragment containing 8 bytes or less of the TCP header. Since 24 is divisible by 8, we got 3 IP fragments; each has 20 bytes of IP header and 8 bytes of TCP header. We can see the three fragments between the fifth and the seventh lines.



Note that if you added -ff (or -f -f), the fragmentation of the data will be multiples of 16. In other words, the 24 bytes of the TCP header, in this case, would be divided over two IP fragments, the first containing 16 bytes and the second containing 8 bytes of the TCP header.

On the other hand, if you prefer to increase the size of your packets to make them look innocuous, you can use the option --data-length NUM, where num specifies the number of bytes you want to append to your packets.

### Idle scan

Spoofing the source IP address can be a great approach to scanning stealthily. However, spoofing will only work in specific network setups. It requires you to be in a position where you can monitor the traffic. Considering these limitations, spoofing your IP address can have little use; however, we can give it an upgrade with the idle scan.

The idle scan, or zombie scan, requires an idle system connected to the network that you can communicate with. Practically, Nmap will make each probe appear as if coming from the idle (zombie) host, then it will check for indicators whether the idle (zombie) host received any response to the spoofed probe. This is accomplished by checking the IP identification (IP ID) value in the IP header. You can run an idle scan using nmap -sI ZOMBIE_IP MACHINE_IP, where ZOMBIE_IP is the IP address of the idle host (zombie).

The idle (zombie) scan requires the following three steps to discover whether a port is open:

Trigger the idle host to respond so that you can record the current IP ID on the idle host.
Send a SYN packet to a TCP port on the target. The packet should be spoofed to appear as if it was coming from the idle host (zombie) IP address.
Trigger the idle machine again to respond so that you can compare the new IP ID with the one received earlier.
Let’s explain with figures. In the figure below, we have the attacker system probing an idle machine, a multi-function printer. By sending a SYN/ACK, it responds with an RST packet containing its newly incremented IP ID.



The attacker will send a SYN packet to the TCP port they want to check on the target machine in the next step. However, this packet will use the idle host (zombie) IP address as the source. Three scenarios would arise. In the first scenario, shown in the figure below, the TCP port is closed; therefore, the target machine responds to the idle host with an RST packet. The idle host does not respond; hence its IP ID is not incremented.



In the second scenario, as shown below, the TCP port is open, so the target machine responds with a SYN/ACK to the idle host (zombie). The idle host responds to this unexpected packet with an RST packet, thus incrementing its IP ID.



In the third scenario, the target machine does not respond at all due to firewall rules. This lack of response will lead to the same result as with the closed port; the idle host won’t increase the IP ID.

For the final step, the attacker sends another SYN/ACK to the idle host. The idle host responds with an RST packet, incrementing the IP ID by one again. The attacker needs to compare the IP ID of the RST packet received in the first step with the IP ID of the RST packet received in this third step. If the difference is 1, it means the port on the target machine was closed or filtered. However, if the difference is 2, it means that the port on the target was open.

It is worth repeating that this scan is called an idle scan because choosing an idle host is indispensable for the accuracy of the scan. If the “idle host” is busy, all the returned IP IDs would be useless. Moreover, the idle host should be on the same network as the target machine. Finally, the idle host should not be behind a stateful firewall, as this would render the scan useless.

You might consider adding --reason if you want Nmap to provide more details regarding its reasoning and conclusions. Consider the two scans below to the system; however, the latter adds --reason.

Providing the --reason flag gives us the explicit reason why Nmap concluded that the system is up or a particular port is open. In this console output above, we can see that this system is considered online because Nmap “received arp-response.” On the other hand, we know that the SSH port is deemed to be open because Nmap received a “syn-ack” packet back.

For more detailed output, you can consider using -v for verbose output or -vv for even more verbosity.

If -vv does not satisfy your curiosity, you can use -d for debugging details or -dd for even more details. You can guarantee that using -d will create an output that extends beyond a single screen.

This room covered the following types of scans.

| Port Scan Type       | Example Command                                         |
|----------------------|---------------------------------------------------------|
| TCP Null Scan        | sudo nmap -sN 10.10.227.47                              |
| TCP FIN Scan         | sudo nmap -sF 10.10.227.47                              |
| TCP Xmas Scan        | sudo nmap -sX 10.10.227.47                              |
| TCP Maimon Scan      | sudo nmap -sM 10.10.227.47                              |
| TCP ACK Scan         | sudo nmap -sA 10.10.227.47                              |
| TCP Window Scan      | sudo nmap -sW 10.10.227.47                              |
| Custom TCP Scan      | sudo nmap --scanflags URGACKPSHRSTSYNFIN 10.10.227.47   |
| Spoofed Source IP    | sudo nmap -S SPOOFED_IP 10.10.227.47                    |
| Spoofed MAC Address  | --spoof-mac SPOOFED_MAC                                 |
| Decoy Scan           | nmap -D DECOY_IP,ME 10.10.227.47                        |
| Idle (Zombie) Scan   | sudo nmap -sI ZOMBIE_IP 10.10.227.47                    |
| Fragment IP data into 8 bytes  | -f                                            |
| Fragment IP data into 16 bytes | -ff                                           |


| Option             | Purpose                  |
|--------------------|--------------------------|
| --source-port PORT_NUM | specify source port number |
| --data-length NUM  | append random data to reach given length |


These scan types rely on setting TCP flags in unexpected ways to prompt ports for a reply. Null, FIN, and Xmas scan provoke a response from closed ports, while Maimon, ACK, and Window scans provoke a response from open and closed ports.

| Option   | Purpose                           |
|----------|-----------------------------------|
| --reason | explains how Nmap made its conclusion |
| -v       | verbose                           |
| -vv      | very verbose                      |
| -d       | debugging                         |
| -dd      | more details for debugging        |

Once Nmap discovers open ports, you can probe the available port to detect the running service. Further investigation of open ports is an essential piece of information as the pentester can use it to learn if there are any known vulnerabilities of the service. Join Vulnerabilities 101 to learn more about searching for vulnerable services.

Adding -sV to your Nmap command will collect and determine service and version information for the open ports. You can control the intensity with --version-intensity LEVEL where the level ranges between 0, the lightest, and 9, the most complete. -sV --version-light has an intensity of 2, while -sV --version-all has an intensity of 9.

It is important to note that using -sV will force Nmap to proceed with the TCP 3-way handshake and establish the connection. The connection establishment is necessary because Nmap cannot discover the version without establishing a connection fully and communicating with the listening service. In other words, stealth SYN scan -sS is not possible when -sV option is chosen.

The console output below shows a simple Nmap stealth SYN scan with the -sV option. Adding the -sV option leads to a new column in the output showing the version for each detected service. For instance, in the case of TCP port 22 being open, instead of 22/tcp open ssh, we obtain 22/tcp open ssh OpenSSH 6.7p1 Debian 5+deb8u8 (protocol 2.0). Notice that the SSH protocol is guessed as the service because TCP port 22 is open; Nmap didn’t need to connect to port 22 to confirm. However, -sV required connecting to this open port to grab the service banner and any version information it can get, such as nginx 1.6.2. Hence, unlike the service column, the version column is not a guess.

OS Detection
Nmap can detect the Operating System (OS) based on its behaviour and any telltale signs in its responses. OS detection can be enabled using -O; this is an uppercase O as in OS. In this example, we ran nmap -sS -O 10.10.27.43 on the AttackBox. Nmap detected the OS to be Linux 3.X, and then it guessed further that it was running kernel 3.13.

The system that we scanned and attempted to detect its OS version is running kernel version 3.16. Nmap was able to make a close guess in this case. In another case, we scanned a Fedora Linux system with kernel 5.13.14; however, Nmap detected it as Linux 2.6.X. The good news is that Nmap detected the OS correctly; the not-so-good news is that the kernel version was wrong.

The OS detection is very convenient, but many factors might affect its accuracy. First and foremost, Nmap needs to find at least one open and one closed port on the target to make a reliable guess. Furthermore, the guest OS fingerprints might get distorted due to the rising use of virtualization and similar technologies. Therefore, always take the OS version with a grain of salt.

Traceroute
If you want Nmap to find the routers between you and the target, just add --traceroute. In the following example, Nmap appended a traceroute to its scan results. Note that Nmap’s traceroute works slightly different than the traceroute command found on Linux and macOS or tracert found on MS Windows. Standard traceroute starts with a packet of low TTL (Time to Live) and keeps increasing until it reaches the target. Nmap’s traceroute starts with a packet of high TTL and keeps decreasing it.

In the following example, we executed nmap -sS --traceroute 10.10.27.43 on the AttackBox. We can see that there are no routers/hops between the two as they are connected directly.

A script is a piece of code that does not need to be compiled. In other words, it remains in its original human-readable form and does not need to be converted to machine language. Many programs provide additional functionality via scripts; moreover, scripts make it possible to add custom functionality that did not exist via the built-in commands. Similarly, Nmap provides support for scripts using the Lua language. A part of Nmap, Nmap Scripting Engine (NSE) is a Lua interpreter that allows Nmap to execute Nmap scripts written in Lua language. However, we don’t need to learn Lua to make use of Nmap scripts.

Your Nmap default installation can easily contain close to 600 scripts. Take a look at your Nmap installation folder. On the AttackBox, check the files at /usr/share/nmap/scripts, and you will notice that there are hundreds of scripts conveniently named starting with the protocol they target. We listed all the scripts starting with the HTTP on the AttackBox in the console output below; we found around 130 scripts starting with http. With future updates, you can only expect the number of installed scripts to increase.

You can specify to use any or a group of these installed scripts; moreover, you can install other user’s scripts and use them for your scans. Let’s begin with the default scripts. You can choose to run the scripts in the default category using --script=default or simply adding -sC. In addition to default, categories include auth, broadcast, brute, default, discovery, dos, exploit, external, fuzzer, intrusive, malware, safe, version, and vuln. A brief description is shown in the following table.

| Script Category | Description |
|-----------------|-------------|
| auth            | Authentication related scripts |
| broadcast       | Discover hosts by sending broadcast messages |
| brute           | Performs brute-force password auditing against logins |
| default         | Default scripts, same as -sC |
| discovery       | Retrieve accessible information, such as database tables and DNS names |
| dos             | Detects servers vulnerable to Denial of Service (DoS) |
| exploit         | Attempts to exploit various vulnerable services |
| external        | Checks using a third-party service, such as Geoplugin and Virustotal |
| fuzzer          | Launch fuzzing attacks |
| intrusive       | Intrusive scripts such as brute-force attacks and exploitation |
| malware         | Scans for backdoors |
| safe            | Safe scripts that won’t crash the target |
| version         | Retrieve service versions |
| vuln            | Checks for vulnerabilities or exploit vulnerable services |

Some scripts belong to more than one category. Moreover, some scripts launch brute-force attacks against services, while others launch DoS attacks and exploit systems. Hence, it is crucial to be careful when selecting scripts to run if you don’t want to crash services or exploit them.

We use Nmap to run a SYN scan against 10.10.4.80 and execute the default scripts in the console shown below. The command is sudo nmap -sS -sC 10.10.4.80, where -sC will ensure that Nmap will execute the default scripts following the SYN scan. There are new details that appear below. Take a look at the SSH service at port 22; Nmap recovered all four public keys related to the running server. Consider another example, the HTTP service at port 80; Nmap retrieved the default page title. We can see that the page has been left as default.


Nmap done: 1 IP address (1 host up) scanned in 2.21 seconds
You can also specify the script by name using --script "SCRIPT-NAME" or a pattern such as --script "ftp*", which would include ftp-brute. If you are unsure what a script does, you can open the script file with a text reader, such as less, or a text editor. In the case of ftp-brute, it states: “Performs brute force password auditing against FTP servers.” You have to be careful as some scripts are pretty intrusive. Moreover, some scripts might be for a specific server and, if chosen at random, will waste your time with no benefit. As usual, make sure that you are authorized to launch such tests on the target server.

Let’s consider a benign script, http-date, which we guess would retrieve the http server date and time, and this is indeed confirmed in its description: “Gets the date from HTTP-like services. Also, it prints how much the date differs from local time…” On the AttackBox, we execute sudo nmap -sS -n --script "http-date" 10.10.4.80 as shown in the console below.

Nmap done: 1 IP address (1 host up) scanned in 1.78 seconds
Finally, you might expand the functionality of Nmap beyond the official Nmap scripts; you can write your script or download Nmap scripts from the Internet. Downloading and using a Nmap script from the Internet holds a certain level of risk. So it is a good idea not to run a script from an author you don’t trust.

Whenever you run a Nmap scan, it is only reasonable to save the results in a file. Selecting and adopting a good naming convention for your filenames is also crucial. The number of files can quickly grow and hinder your ability to find a previous scan result. The three main formats are:

Normal
Grepable (grepable)
XML
There is a fourth one that we cannot recommend:

Script Kiddie

Normal
As the name implies, the normal format is similar to the output you get on the screen when scanning a target. You can save your scan in normal format by using -oN FILENAME; N stands for normal. Here is an example of the result.

```text
pentester@TryHackMe$ cat 10.10.117.59_scan.nmap 
# Nmap 7.60 scan initiated Fri Sep 10 05:14:19 2021 as: nmap -sS -sV -O -oN 10.10.117.59_scan MACHINE_IP
Nmap scan report for 10.10.117.59
Host is up (0.00086s latency).
Not shown: 994 closed ports
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 6.7p1 Debian 5+deb8u8 (protocol 2.0)
25/tcp  open  smtp    Postfix smtpd
80/tcp  open  http    nginx 1.6.2
110/tcp open  pop3    Dovecot pop3d
111/tcp open  rpcbind 2-4 (RPC #100000)
143/tcp open  imap    Dovecot imapd
MAC Address: 02:A0:E7:B5:B6:C5 (Unknown)
Device type: general purpose
Running: Linux 3.X
OS CPE: cpe:/o:linux:linux_kernel:3.13
OS details: Linux 3.13
Network Distance: 1 hop
Service Info: Host:  debra2.thm.local; OS: Linux; CPE: cpe:/o:linux:linux_kernel

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Sep 10 05:14:28 2021 -- 1 IP address (1 host up) scanned in 9.99 seconds
```

Grepable
The grepable format has its name from the command grep; grep stands for Global Regular Expression Printer. In simple terms, it makes filtering the scan output for specific keywords or terms efficient. You can save the scan result in grepable format using -oG FILENAME. The scan output, displayed above in normal format, is shown in the console below using grepable format. The normal output is 21 lines; however, the grepable output is only 4 lines. The main reason is that Nmap wants to make each line meaningful and complete when the user applies grep. As a result, in grepable output, the lines are so long and are not convenient to read compared to normal output.

```
Pentester Terminal
pentester@TryHackMe$ cat 10.10.117.59_scan.gnmap 
# Nmap 7.60 scan initiated Fri Sep 10 05:14:19 2021 as: nmap -sS -sV -O -oG 10.10.117.59_scan MACHINE_IP
Host: 10.10.117.59	Status: Up
Host: MACHINE_IP	Ports: 22/open/tcp//ssh//OpenSSH 6.7p1 Debian 5+deb8u8 (protocol 2.0)/, 25/open/tcp//smtp//Postfix smtpd/, 80/open/tcp//http//nginx 1.6.2/, 110/open/tcp//pop3//Dovecot pop3d/, 111/open/tcp//rpcbind//2-4 (RPC #100000)/, 143/open/tcp//imap//Dovecot imapd/	Ignored State: closed (994)	OS: Linux 3.13	Seq Index: 257	IP ID Seq: All zeros
# Nmap done at Fri Sep 10 05:14:28 2021 -- 1 IP address (1 host up) scanned in 9.99 seconds
An example use of grep is grep KEYWORD TEXT_FILE; this command will display all the lines containing the provided keyword. Let’s compare the output of using grep on normal output and grepable output. You will notice that the former does not provide the IP address of the host. Instead, it returned 80/tcp open http nginx 1.6.2, making it very inconvenient if you are sifting through the scan results of multiple systems. However, the latter provides enough information, such as the host’s IP address, in each line to make it complete.
```

```
Pentester Terminal
pentester@TryHackMe$ grep http 10.10.117.59_scan.nmap 
80/tcp  open  http    nginx 1.6.2
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Pentester Terminal
pentester@TryHackMe$ grep http 10.10.117.59_scan.gnmap 
Host: 10.10.117.59	Ports: 22/open/tcp//ssh//OpenSSH 6.7p1 Debian 5+deb8u8 (protocol 2.0)/, 25/open/tcp//smtp//Postfix smtpd/, 80/open/tcp//http//nginx 1.6.2/, 110/open/tcp//pop3//Dovecot pop3d/, 111/open/tcp//rpcbind//2-4 (RPC #100000)/, 143/open/tcp//imap//Dovecot imapd/	Ignored State: closed (994)	OS: Linux 3.13	Seq Index: 257	IP ID Seq: All zeros
```

XML
The third format is XML. You can save the scan results in XML format using -oX FILENAME. The XML format would be most convenient to process the output in other programs. Conveniently enough, you can save the scan output in all three formats using -oA FILENAME to combine -oN, -oG, and -oX for normal, grepable, and XML.

| Option               | Meaning                                         |
|----------------------|-------------------------------------------------|
| -sV                  | determine service/version info on open ports    |
| -sV --version-light  | try the most likely probes (2)                  |
| -sV --version-all    | try all available probes (9)                    |
| -O                   | detect OS                                       |
| --traceroute         | run traceroute to target                        |
| --script=SCRIPTS     | Nmap scripts to run                             |
| -sC or --script=default | run default scripts                          |
| -A                   | equivalent to -sV -O -sC --traceroute            |
| -oN                  | save output in normal format                    |
| -oG                  | save output in grepable format                  |
| -oX                  | save output in XML format                       |
| -oA                  | save output in normal, XML and Grepable formats |