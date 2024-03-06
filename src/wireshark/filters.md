# Wireshark filters

Wireshark filters are used to filter out packets from a packet capture according to a set of rules. The rules can be based on various fields such as IP addresses, port numbers, protocols, etc.

### IP address

```bash
ip.addr ==
```

### Port number

```bash
tcp.port == 80
```

### Protocol

```bash
ip.proto == 6
```

### IP address and port number

```bash
ip.addr ==
tcp.port ==
```

### IP address and protocol

```bash
ip.addr ==
ip.proto ==
```

### Port number and protocol

```bash
tcp.port ==
ip.proto ==
```

### IP address, port number, and protocol

```bash
ip.addr ==
tcp.port ==
ip.proto ==
```

### IP address range

```bash
ip.addr >=
ip.addr <=
```

### Port number range

```bash
tcp.port >=
tcp.port <=
```

### Protocol range

```bash
ip.proto >=
ip.proto <=
```

### IP address and port number range

```bash
ip.addr >=
ip.addr <=
tcp.port >=
tcp.port <=
```

### IP address and protocol range

```bash
ip.addr >=
ip.addr <=
ip.proto >=
ip.proto <=
```

### Port number and protocol range

```bash
tcp.port >=
tcp.port <=
ip.proto >=
ip.proto <=
```

### IP address, port number, and protocol range

```bash
ip.addr >=
ip.addr <=
tcp.port >=
tcp.port <=
ip.proto >=
ip.proto <=
```

## Fileter operators

### Logical AND

```bash
&&
```

### Logical OR

```bash
||
```

### Logical NOT

```bash
!
```

### Logical XOR

```bash
xor
```

### Logical NAND

```bash
nand
```

### Logical NOR

```bash
nor
```

### Logical XNOR

```bash
xnor
```

### Logical NOT AND

```bash
!&&
```

### Logical NOT OR

```bash
!||
```

### Logical NOT XOR

```bash
!xor
```

### Logical NOT NAND

```bash
!nand
```

### Logical NOT NOR

```bash
!nor
```

### Logical NOT XNOR

```bash
!xnor
```

### Logical AND NOT

```bash
&&!
```

### Logical OR NOT

```bash
||!
```

### Logical XOR NOT

```bash
xor!
```

### Logical NAND NOT

```bash
nand!
```

### Logical NOR NOT

```bash
nor!
```

### Logical XNOR NOT

```bash
xnor!
```

### Logical AND XOR

```bash
&&xor
```

### Logical AND NAND

```bash
&&nand
```

### Logical AND NOR

```bash
&&nor
```

### Logical AND XNOR

```bash
&&xnor
```

### Logical OR XOR

```bash
||xor
```

### Logical OR NAND

```bash
||nand
```

### Logical OR NOR

```bash
||nor
```

### Logical OR XNOR

```bash
||xnor
```

### Logical XOR NAND

```bash
xornand
```

### Logical XOR NOR

```bash
xornor
```

### Logical XOR XNOR

```bash
xorxnor
```

### Logical NAND NOR

```bash
nandnor
```

### Logical NAND XNOR

```bash
nandxnor
```

### Logical NOR XNOR

```bash
norxnor
```

### Logical AND NOT XOR

```bash
&&!xor
```

### Logical AND NOT NAND

```bash
&&!nand
```

### Logical AND NOT NOR

```bash
&&!nor
```

### Logical AND NOT XNOR

```bash
&&!xnor
```

### Logical OR NOT XOR

```bash
!||xor
```

### Logical OR NOT NAND

```bash
!||nand
```

### Logical OR NOT NOR

```bash
!||nor
```

### Logical OR NOT XNOR

```bash
!||xnor
```

### Logical XOR NOT NAND

```bash
xor!nand
```

### Logical XOR NOT NOR

```bash
xor!nor
```

### Logical XOR NOT XNOR

```bash
xor!xnor
```

### Logical NAND NOT NOR

```bash
nand!nor
```

### Logical NAND NOT XNOR

```bash
nand!xnor
```

### Logical NOR NOT XNOR

```bash
nor!xnor
```

### Logical AND XOR NOT

```bash
&&xor!
```

### Logical AND NAND NOT

```bash
&&nand!
```

### Logical AND NOR NOT

```bash
&&nor!
```

### Logical AND XNOR NOT

```bash
&&xnor!
```

### Logical OR XOR NOT

```bash
||xor!
```

### Logical OR NAND NOT

```bash
||nand!
```

### Logical OR NOR NOT

```bash
||nor!
```

### Logical OR XNOR NOT

```bash
||xnor!
```

### Logical XOR NAND NOT

```bash
xor!nand!
```

### Logical XOR NOR NOT

```bash
xor!nor!
```

### Logical XOR XNOR NOT

```bash
xor!xnor!
```

### Logical NAND NOR NOT

```bash
nand!nor!
```

### Logical NAND XNOR NOT

```bash
nand!xnor!
```

### Logical NOR XNOR NOT

```bash
nor!xnor!
```


Wireshark only has a few that you will need to be familiar with:

and - operator: and / &&
or - operator: or / ||
equals - operator: eq / ==
not equal - operator: ne / !=
greater than - operator: gt /  >
less than - operator: lt / <

The operators can be used in combination with each other to create complex filters. For example, to filter out all packets that are not from a specific IP address and are not destined for a specific port, you can use the following filter:

```bash
ip.addr !=
tcp.port !=
```

ip.addr == <IP Address>

tcp.port == <Port Number>

ip.proto == <Protocol Number>

ip.addr == <IP Address> && tcp.port == <Port Number>

ip.addr == <IP Address> && ip.proto == <Protocol Number>

tcp.port == <Port Number> && ip.proto == <Protocol Number>

ip.addr == <IP Address> && tcp.port == <Port Number> && ip.proto == <Protocol Number>

ip.addr >= <Start IP Address> && ip.addr <= <End IP Address>

tcp.port >= <Start Port Number> && tcp.port <= <End Port Number>

ip.proto >= <Start Protocol Number> && ip.proto <= <End Protocol Number>

ip.addr >= <Start IP Address> && ip.addr <= <End IP Address> && tcp.port >= <Start Port Number> && tcp.port <= <End Port Number>

ip.addr >= <Start IP Address> && ip.addr <= <End IP Address> && ip.proto >= <Start Protocol Number> && ip.proto <= <End Protocol Number>

tcp.port >= <Start Port Number> && tcp.port <= <End Port Number> && ip.proto >= <Start Protocol Number> && ip.proto <= <End Protocol Number>

ip.addr >= <Start IP Address> && ip.addr <= <End IP Address> && tcp.port >= <Start Port Number> && tcp.port <= <End Port Number> && ip.proto >= <Start Protocol Number> && ip.proto <= <End Protocol Number>

