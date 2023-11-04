# ffuf

Fuzz Faster U Fool is a great tool for fuzzing. It is written in Go and is very
fast. It is also very easy to use. It is a swiss army knife for fuzzing, and 
can be used for many purposes. It can be used for fuzzing web applications, 
DNS, and even file systems.

The pther side of this is that is an automated tool. It is not a tool that is
allowed to be used in many bug bounty programs, but you can bypass this by
using:

```shell
ffuf -t 1
```

```text
ffuf --help | rg threads

-t     Number of concurrent threads. (default: 40)
```

This will make ffuf run in a single thread, which is allowed in most bug bounty
programs. Default is 40 threads. That's why it's so fast. The exact number of
threads that is allowed is not known, but it's usually 1-5.