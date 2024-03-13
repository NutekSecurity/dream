# Basic SMB

What is SMB?

SMB - Server Message Block Protocol - is a client-server communication protocol used for sharing access to files, printers, serial ports and other resources on a network. [source]

Servers make file systems and other resources (printers, named pipes, APIs) available to clients on the network. Client computers may have their own hard disks, but they also want access to the shared file systems and printers on the servers.

The SMB protocol is known as a response-request protocol, meaning that it transmits multiple messages between the client and server to establish a connection. Clients connect to servers using TCP/IP (actually NetBIOS over TCP/IP as specified in RFC1001 and RFC1002), NetBEUI or IPX/SPX.

How does SMB work?











Once they have established a connection, clients can then send commands (SMBs) to the server that allow them to access shares, open files, read and write files, and generally do all the sort of things that you want to do with a file system. However, in the case of SMB, these things are done over the network.

What runs SMB?

Microsoft Windows operating systems since Windows 95 have included client and server SMB protocol support. Samba, an open source server that supports the SMB protocol, was released for Unix systems.

What is Samba?

Samba is a free software re-implementation of the SMB networking protocol, and was originally developed by Andrew Tridgell. Samba provides file and print services for various Microsoft Windows clients and can integrate with a Windows Server domain, either as a Domain Controller (DC) or as a domain member. As of version 4, it supports Active Directory and Microsoft Windows NT domains.

Samba runs on most Unix and Unix-like systems, such as Linux, Solaris, AIX and the BSD variants, including Apple's macOS Server, and OS/2.

Samba is standard on nearly all distributions of Linux and is commonly included as a basic system service on other Unix-based operating systems as well. Samba is released under the terms of the GNU General Public License. The name Samba comes from SMB (Server Message Block), the name of the standard protocol used by the Microsoft Windows network file system.

What is the difference between SMB and CIFS?


CIFS (Common Internet File System) is a dialect of SMB. Both SMB and CIFS are also available on VMS, several versions of Unix, and other operating systems. CIFS is a public or open variation of the Server Message Block Protocol (SMB) developed and used by Microsoft, and it uses the TCP/IP protocol. The term CIFS does not refer to a single protocol, but to a family of protocols, including the following:

- The Core Protocol
- The NT LM Security Support Provider (NTLMSSP) Authentication Protocol
- The Distributed File System (DFS) Referral Protocol
- The Remote Procedure Call (RPC) Protocol
- The Print Server Protocol
- The Mail Slot Protocol
- The Net Logon Protocol
- The Backup Protocol
- The Change Notify Protocol
- The Service Control Protocol
- The Browser Protocol
- The Remote Administration Protocol
- The WINS Replication Protocol
- The Messaging Name Resolution Protocol
- The Transaction Protocol
- The Remote Registry Protocol
- The File and Print Sharing Protocol
- The Distributed Link Tracking Protocol
- The Shadow Copy Protocol
- The DFS Replication Protocol
- The Branch Cache Protocol
- The Federated File System Protocol
- The SmbDirect Protocol
- The SMB Encryption Protocol
- The SMB Compression Protocol
- The SMB Signing Protocol
- The SMB Encryption Protocol
- The SMB Compression Protocol
- The SMB Signing Protocol


What is the difference between SMB and NFS?

SMB and NFS are two network file sharing protocols. The main difference between the two is that SMB is used by Windows and NFS is used by Unix. SMB is a network file sharing protocol that allows applications to read and write to files and to request services from server programs in a computer network. NFS is a network file system protocol that allows a user on a client computer to access files over a network in the same way they would access a local storage file.

Lets Get Started

Before we begin, make sure to deploy the room and give it some time to boot. Please be aware, this can take up to five minutes so be patient!

Enumeration

Enumeration is the process of gathering information on a target in order to find potential attack vectors and aid in exploitation.

This process is essential for an attack to be successful, as wasting time with exploits that either don't work or can crash the system can be a waste of energy. Enumeration can be used to gather usernames, passwords, network information, hostnames, application data, services, or any other information that may be valuable to an attacker.

SMB

Typically, there are SMB share drives on a server that can be connected to and used to view or transfer files. SMB can often be a great starting point for an attacker looking to discover sensitive information — you'd be surprised what is sometimes included on these shares.



Port Scanning

The first step of enumeration is to conduct a port scan, to find out as much information as you can about the services, applications, structure and operating system of the target machine.

If you haven't already looked at port scanning, I recommend checking out the Nmap room here.

Enum4Linux

Enum4linux is a tool used to enumerate SMB shares on both Windows and Linux systems. It is basically a wrapper around the tools in the Samba package and makes it easy to quickly extract information from the target pertaining to SMB. It's installed by default on Parrot and Kali, however if you need to install it, you can do so from the official github.

The syntax of Enum4Linux is nice and simple: "enum4linux [options] ip"

| Tag | Function                               |
|-----|----------------------------------------|
| -U  | get userlist                           |
| -M  | get machine list                       |
| -N  | get namelist dump (different from -U and -M) |
| -S  | get sharelist                          |
| -P  | get password policy information        |
| -G  | get group and member list              |
| -a  | all of the above (full basic enumeration) |

Now we understand our enumeration tools, let's get started!

Types of SMB Exploit

While there are vulnerabilities such as CVE-2017-7494 that can allow remote code execution by exploiting SMB, you're more likely to encounter a situation where the best way into a system is due to misconfigurations in the system. In this case, we're going to be exploiting anonymous SMB share access- a common misconfiguration that can allow us to gain information that will lead to a shell.

Method Breakdown

So, from our enumeration stage, we know:

    - The SMB share location

    - The name of an interesting SMB share

SMBClient

Because we're trying to access an SMB share, we need a client to access resources on servers. We will be using SMBClient because it's part of the default samba suite. While it is available by default on Kali and Parrot, if you do need to install it, you can find the documentation here.

We can remotely access the SMB share using the syntax:

smbclient //[IP]/[SHARE]

Followed by the tags:

-U [name] : to specify the user

-p [port] : to specify the port

Got it? Okay, let's do this!

