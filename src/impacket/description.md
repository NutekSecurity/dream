# Impacket

[Fortra](https://www.coresecurity.com/core-labs/open-source-tools/impacket)

Impacket is a collection of Python classes for working with network protocols. Impacket is focused on providing low-level programmatic access to the packets and for some protocols (e.g. SMB1-3 and MSRPC), the protocol implementation itself. Packets can be constructed from scratch, as well as parsed from raw data, and the object oriented API makes it simple to work with deep hierarchies of protocols. The library provides a set of tools as examples of what can be done within the context of this library.

## Installation

```bash
pipx install impacket
```

## Usage

```python
from impacket import smb
```

## Features

- SMB1-3 and MSRPC
- NTLM and Kerberos authentication
- NMB and SMB NetBIOS
- DCE/RPC
- LLMNR and NBT-NS
- NTLMSSP
- AJP Protocol
- LDAP
- KRB5
- SMB2
- SMB3
- WMI
- TDS
- HTTP

