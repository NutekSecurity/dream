# Linux

Where is Linux Used?
It's fair to say that Linux is a lot more intimidating to approach than Operating System's (OSs) such as Windows. Both variants have their own advantages and disadvantages. For example, Linux is considerably much more lightweight and you'd be surprised to know that there's a good chance you've used Linux in some form or another every day! Linux powers things such as:

Websites that you visit
Car entertainment/control panels
Point of Sale (PoS) systems such as checkout tills and registers in shops
Critical infrastructures such as traffic light controllers or industrial sensors

Flavours of Linux
The name "Linux" is actually an umbrella term for multiple OS's that are based on UNIX (another operating system). Thanks to UNIX being open-source, variants of Linux comes in all shapes and sizes - suited best for what the system is being used for.

For example, Ubuntu & Debian are some of the more commonplace distributions of Linux because it is so extensible. I.e. you can run Ubuntu as a server (such as websites & web applications) or as a fully-fledged desktop. For this series, we're going to be using Ubuntu.

Ubuntu Server can run on systems with only 512MB of RAM

Similar to how you have different versions Windows (7, 8 and 10), there are many different versions/distributions of Linux.

This room has a Ubuntu Linux machine that you can interact with all within your browser whilst following along with this room's material. 

However, to get started, simply press the green "Start Machine" button on the top-right of this task indicated by the arrow on the right: 

Once deployed, a card will appear at the top of the room:



This contains all of the information for the machine deployed in the room including the IP address and expiry timer - along with buttons to manage the machine. Remember to "Terminate" a machine once you are done with the room. More information on this can be found in the tutorial room.

For now, press "Start Machine" where you will be able to interact with your own Linux machine within your browser whilst following along with this room: 

Answer the questions below
I've deployed my first Linux machine!

As we previously discussed, a large selling point of using OSs such as Ubuntu is how lightweight they can be. This, of course, doesn't come without its disadvantages, where for example, often there is no GUI (Graphical User Interface) or what is also known as a desktop environment that we can use to interact with the machine (unless it has been installed). A large part of interacting with these systems is using the "Terminal".

The "Terminal" is purely text-based and is intimidating at first. However, if we break down some of the commands, after some time, you quickly become familiar with using the terminal!

This is what a terminal looks like
tryhackme@linux1:~$ enter commands here
We need to be able to do basic functions like navigate to files, output their contents and make files! The commands to do so are self-explanatory (once you know what they are of course...)

Let's get started with two of the first commands which I have broken down in the table below:

Command	Description
echo	Output any text that we provide
whoami	Find out what user we're currently logged in as!


See the snippets below for an example of each command being used...


Using echo
tryhackme@linux1:~$ echo "Hello Friend!"
Using whoami to find out the username of who we're logged in as
tryhackme@linux1:~$ whoami
Try this on your Linux machine now!

So far we've only covered the "echo" and "whoami" commands. Not all that useful when you consider things that we need to do - including navigating the filesystem, read and write to it as well.

In this task, we're going to be learning the commands so that we can do just that. Just like the previous task, I'll display the commands in the table in the next heading & show examples of these commands being used.



Interacting With the Filesystem
As I previously stated, being able to navigate the machine that you are logged into without relying on a desktop environment is pretty important. After all, what's the point of logging in if we can't go anywhere?

Command	Full Name
ls	listing
cd	change directory
cat	concatenate
pwd	print working directory


Listing Files in Our Current Directory (ls)
Before we can do anything such as finding out the contents of any files or folders, we need to know what exists in the first place. This can be done using the "ls" command (short for listing)

Using "ls" to to list the contents of the current directory
tryhackme@linux1:~$ ls
'Important Files' 'My Documents' Notes Pictures

In the screenshot above, we can see there are the following directories/folders:

Important Files
My Documents
Notes
Pictures
Great! You can probably take a guess as to what to expect a folder to contain given by its name.

Pro tip: You can list the contents of a directory without having to navigate to it by using ls and the name of the directory. I.e. ls Pictures


Changing Our Current Directory (cd)
Now that we know what folders exist, we need to use the "cd" command (short for change directory) to change to that directory. Say if I wanted to open the "Pictures" directory - I'd do "cd Pictures". Where again, we want to find out the contents of this "Pictures" directory and to do so, we'd use "ls" again:

Listing our new directory after we have used "cd"
tryhackme@linux1:~/Pictures$ ls
dog_picture1.jpg dog_picture2.jpg dog_picture3.jpg dog_picture4.jpg
In this case, it looks like there are 4 pictures of dogs!



Outputting the Contents of a File (cat)
Whilst knowing about the existence of files is great — it's not all that useful unless we're able to view the contents of them.

We will come on to discuss some of the tools available to us that allows us to transfer files from one machine to another in a later room. But for now, we're going to talk about simply seeing the contents of text files using a command called "cat".

"Cat" is short for concatenating & is a fantastic way for us to output the contents of files (not just text files!).

In the screenshot below, you can see how I have combined the use of "ls" to list the files within a directory called "Documents":

Using "ls" to to list the contents of the current directory
tryhackme@linux1:~/Documents$ ls
todo.txt
tryhackme@linux1:~/Documents$ cat todo.txt
Here's something important for me to do later!
We've applied some knowledge from earlier in this task to do the following:

Used "ls" to let us know what files are available in the "Documents" folder of this machine. In this case, it is called "todo.txt".
We have then used cat todo.txt to concatenate/output the contents of this "todo.txt" file, where the contents are "Here's something important for me to do later!"
Pro tip: You can use cat to output the contents of a file within directories without having to navigate to it by using cat and the name of the directory. I.e. cat /home/ubuntu/Documents/todo.txt

Sometimes things like usernames, passwords (yes - really...), flags or configuration settings are stored within files where "cat" can be used to retrieve these.



Finding out the full Path to our Current Working Directory (pwd)
You'll notice as you progress through navigating your Linux machine, the name of the directory that you are currently working in will be listed in your terminal.

It's easy to lose track of where we are on the filesystem exactly, which is why I want to introduce "pwd". This stands for print working directory.

Using the example machine from before, we are currently in the "Documents" folder — but where is this exactly on the Linux machine's filesystem? We can find this out using this "pwd" command like within the screenshot below:

Using "pwd" to list the full path of the current directory
tryhackme@linux1:~/Documents$ pwd
/home/ubuntu/Documents
tryhackme@linux1:~/Documents$
Let's break this down:

We already know we're in "Documents" thanks to our terminal, but at this point in time, we have no idea where "Documents" is stored so that we can get back to it easily in the future.
I have used the "pwd" (print working directory) command to find the full file path of this "Documents" folder.
We're helpfully told by Linux that this "Documents" directory is stored at "/home/ubuntu/Documents" on the machine — great to know!
Now in the future, if we find ourselves in a different location, we can just use cd /home/ubuntu/Documents to change our working directory to this "Documents" directory.

Although it doesn't seem like it so far, one of the redeeming features of Linux is truly how efficient you can be with it. With that said, you can only be as efficient as you are familiar with it of course. As you interact with OSs such as Ubuntu over time, essential commands like those we've already covered will start to become muscle-memory.

One fantastic way to show just how efficient you can be with systems like this is using a set of commands to quickly search for files across the entire system that our user has access to. No need to consistently use cd and ls to find out what is where. Instead, we can use commands such as find to automate things like this for us!

This is where Linux starts to become a bit more intimidating to approach -- but we'll break this down and ease you into it.

Using Find
The find command is fantastic in the sense that it can be used both very simply or rather complex depending upon what it is you want to do exactly. However, let's stick to the fundamentals first.

Take the snippet below; we can see a list of directories available to us:

Using "ls" to list the contents of the current directory
tryhackme@linux1:~$ ls
Desktop Documents Pictures folder1
tryhackme@linux1:~$

Desktop
Documents
Pictures
folder1
Now, of course, directories can contain even more directories within themselves. It becomes a headache when we're having to look through every single one just to try and look for specific files. We can use find to do just this for us!

Let's start simple and assume that we already know the name of the file we're looking for — but can't remember where it is exactly! In this case, we're looking for "passwords.txt"

If we remember the filename, we can simply use find -name passwords.txt where the command will look through every folder in our current directory for that specific file like so:

Using "find" to find a file with the name of "passwords.txt"
tryhackme@linux1:~$ find -name passwords.txt
./folder1/passwords.txt
tryhackme@linux1:~$

"Find" has managed to find the file — it turns out it is located in folder1/passwords.txt — sweet. But let's say that we don't know the name of the file, or want to search for every file that has an extension such as ".txt". Find let's us do that too!

We can simply use what's known as a wildcard (*) to search for anything that has .txt at the end. In our case, we want to find every .txt file that's in our current directory. We will construct a command such as find -name *.txt . Where "Find" has been able to find every .txt file and has then given us the location of each one:

Using "find" to find any file with the extension of ".txt"
tryhackme@linux1:~$ find -name *.txt
./folder1/passwords.txt
./Documents/todo.txt
tryhackme@linux1:~$

Find has managed to find:

"passwords.txt" located within "folder1"
"todo.txt" located within "Documents"
That wasn't so tough, huh!



Using Grep
Another great utility that is a great one to learn about is the use of grep. The grep command allows us to search the contents of files for specific values that we are looking for.

Take for example, the access log of a web server. In this case, the access.log of a web server has 244 entries.

Using "wc" to count the number of entries in "access.log"
tryhackme@linux1:~$ wc -l access.log
244 access.log
tryhackme@linux1:~$
Using a command like cat isn't going to cut it too well here. Let's say for example if we wanted to search this log file to see the things that a certain user/IP address visited? Looking through 244 entries isn't all that efficient considering we want to find a specific value.

We can use grep to search the entire contents of this file for any entries of the value that we are searching for. Going with the example of a web server's access log, we want to see everything that the IP address "81.143.211.90" has visited (note that this is fictional)

Using "grep" to find any entries with the IP address of "81.143.211.90" in "access.log"
tryhackme@linux1:~$ grep "81.143.211.90" access.log
81.143.211.90 - - [25/Mar/2021:11:17 + 0000] "GET / HTTP/1.1" 200 417 "-" "Mozilla/5.0 (Linux; Android 7.0; Moto G(4))"
tryhackme@linux1:~$
"Grep" has searched through this file and has shown us any entries of what we've provided and that is contained within this log file for the IP.

Linux operators are a fantastic way to power up your knowledge of working with Linux. There are a few important operators that are worth noting. We'll cover the basics and break them down accordingly to bite-sized chunks.

At an overview, I'm going to be showcasing the following operators:

Symbol / Operator	Description
&	This operator allows you to run commands in the background of your terminal.
&&	This operator allows you to combine multiple commands together in one line of your terminal.
>	This operator is a redirector - meaning that we can take the output from a command (such as using cat to output a file) and direct it elsewhere.
>>	
This operator does the same function of the > operator but appends the output rather than replacing (meaning nothing is overwritten).

Let's cover these in a bit more detail.


Operator "&"
This operator allows us to execute commands in the background. For example, let's say we want to copy a large file. This will obviously take quite a long time and will leave us unable to do anything else until the file successfully copies.

The "&" shell operator allows us to execute a command and have it run in the background (such as this file copy) allowing us to do other things!



Operator "&&"
This shell operator is a bit misleading in the sense of how familiar is to its partner "&". Unlike the "&" operator, we can use "&&" to make a list of commands to run for example command1 && command2. However, it's worth noting that command2 will only run if command1 was successful.



Operator ">"
This operator is what's known as an output redirector. What this essentially means is that we take the output from a command we run and send that output to somewhere else.

A great example of this is redirecting the output of the echo command that we learned in Task 4. Of course, running something such as echo howdy will return "howdy" back to our terminal — that isn't super useful. What we can do instead, is redirect "howdy" to something such as a new file!

Let's say we wanted to create a file named "welcome" with the message "hey". We can run echo hey > welcome where we want the file created with the contents "hey" like so:

Using the > Operator
tryhackme@linux1:~$ echo hey > welcome
Using cat to output the "welcome" file
tryhackme@linux1:~$ cat welcome
hey
Note: If the file i.e. "welcome" already exists, the contents will be overwritten!


Operator ">>"
This operator is also an output redirector like in the previous operator (>) we discussed. However, what makes this operator different is that rather than overwriting any contents within a file, for example, it instead just puts the output at the end.

Following on with our previous example where we have the file "welcome" that has the contents of "hey". If were to use echo to add "hello" to the file using the > operator, the file will now only have "hello" and not "hey".

The >> operator allows to append the output to the bottom of the file — rather than replacing the contents like so:

Using the >> Operator
tryhackme@linux1:~$ echo hello >> welcome
Using cat to output the "welcome" file
tryhackme@linux1:~$ cat welcome
hey
hello

Nice work on getting to this stage! We covered quite a bit for your first interactions with Linux. However, these are the most essential/functions you're going to be using whenever you interact with a Linux machine.

I hope this room hasn't been too daunting for you to power-on through with. It's as I previously mentioned, you're going to become familiar with these things very quickly because of how often you're going to be using them.

To quickly recap, we've covered the following:

Understanding why Linux is so commonplace today
Interacting with your first-ever Linux machine!
Ran some of the most fundamental commands
Had an introduction to navigating around the filesystem & how we can use commands like find and grep to make finding data even more efficient!
 Power up your commands by learning about some of the important shell operators.
Take some time to have a play around in this room. When you feel a little bit more comfortable, progress onto Linux Fundamentals Part 2

Welcome to the second part of the reworked "Linux Fundamentals" series. We'll be applying our knowledge from the first installment in this series, so I highly recommend you completing that room before proceeding further.

In part 2, we'll be ditching the in-browser functionality and help you get started in what is a fundamental skill in being able to login to and control the terminals of remote machines. Not only this, but the room will also have you:

Unlocking the potential of your first few commands by introducing you to using flags and arguments
Advancing your knowledge of the filesystem to perform some more useful commands such as copying and moving files
Discovering how access to files and folders is managed and how we can determine our access.



Running your first few scripts and executables!

The in-browser functionality was used in Linux Fundamentals Part 1 to get you directly connected to your first ever Linux machine without any hassle.

In fact, the in-browser functionality uses the exact same protocol that we are going to be using today. This protocol is called Secure Shell or SSH for short and is the common means of connecting to and interacting with the command line of a remote Linux machine.

We will be deploying two machines in this room:

Your Linux machine
The TryHackMe AttackBox
What is SSH & how Does it Work?

Secure Shell or SSH simply is a protocol between devices in an encrypted form. Using cryptography, any input we send in a human-readable format is encrypted for travelling over a network -- where it is then unencrypted once it reaches the remote machine, such as in the diagram below.



You can learn about the various types of encryption on a TryHackMe room. But for now, we only need to understand that:

SSH allows us to remotely execute commands on another device remotely.
Any data sent between the devices is encrypted when it is sent over a network such as the Internet
Deploying Your Linux Machine

Press the green "Start Machine" button on the top-right of this task and then scroll to the top of the page to see the deployment information like so:

The IP address displayed is the address of your Linux machine that you will be logging into using SSH. Take note of this for now.

Deploying the TryHackMe AttackBox

Looking at the top of the page, press the "Start AttackBox" button to deploy the TryHackMe AttackBox that we will be interacting with. The TryHackMe AttackBox is a Ubuntu Linux machine that is hosted online in the cloud and can be interacted with via your browser. You will be using this to interact with the machine that you deploy in this task.




Using SSH to Login to Your Linux Machine

The syntax to use SSH is very simple. We only need to provide two things:

1. The IP address of the remote machine

2. Correct credentials to a valid account to login with on the remote machine



For this room, we will be logging in as "tryhackme", whose password is "tryhackme" without the quotation ("") marks. Let's use the IP address of the machine displayed in the card at the top of the room as the IP address and this user, to construct a command to log in to the remote machine using SSH. The command to do so is ssh and then the username of the account, @ the IP address of the machine.

But first, we need to open a terminal on the TryHackMe AttackBox. There is an icon placed on the desktop named "Terminal". And now, we can proceed to input commands.

For example: ssh tryhackme@MACHINE_IP  . Replacing the IP address with the IP address for your Linux target machine. Once executed, we will then be asked to trust the host and then provide a password for the "tryhackme" account, which is also "tryhackme".



Now that we are connected, any commands that we execute will now execute on the remote machine -- not our own.

Note: When you type a password into an ssh login prompt there is no visible feedback -- you will not be able to see any text or symbols appear as you type the password. It is still working, however, so just type the password and press enter to login.

A majority of commands allow for arguments to be provided. These arguments are identified by a hyphen and a certain keyword known as flags or switches.

We'll later discuss how we can identify what commands allow for arguments to be provided and understanding what these do exactly.

When using a command, unless otherwise specified, it will perform its default behaviour. For example, ls lists the contents of the working directory. However, hidden files are not shown. We can use flags and switches to extend the behaviour of commands.

Using our ls example, ls informs us that there is only one folder named "folder1" as highlighted in the screenshot below. Note that the contents in the screenshots below are only examples.

Using ls to view the contents of a directory
tryhackme@linux2:~$ ls
folder1
tryhackme@linux2:~$
However, after using the -a argument (short for --all), we now suddenly have an output with a few more files and folders such as ".hiddenfolder". Files and folders with "." are hidden files.

Using ls to view hidden folders
tryhackme@linux2:~$ ls -a 
.hiddenfolder folder1
tryhackme@linux2:~$
Commands that accept these will also have a --help option. This option will list the possible options that the command accepts, provide a brief description and example of how to use it.

Listing the options we can use with ls
tryhackme@linux2:~$ ls --help
Usage: ls [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).
Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.

Mandatory arguments to long options are mandatory for short options too.
  -a, --all                  do not ignore entries starting with .
  -A, --almost-all           do not list implied . and ..
      --author               with -l, print the author of each file
  -b, --escape               print C-style escapes for nongraphic characters
      --block-size=SIZE      with -l, scale sizes by SIZE when printing them;
                               e.g., '--block-size=M'; see SIZE format below
  -B, --ignore-backups       do not list implied entries ending with ~
  -c                         with -lt: sort by, and show, ctime (time of last
                               modification of file status information);
                               with -l: show ctime and sort by name;
                               otherwise: sort by ctime, newest first
  -C                         list entries by columns
      --color[=WHEN]         colorize the output; WHEN can be 'always' (default
                               if omitted), 'auto', or 'never'; more info below
  -d, --directory            list directories themselves, not their contents
  -D, --dired                generate output designed for Emacs' dired mode
  -f                         do not sort, enable -aU, disable -ls --color
  -F, --classify             append indicator (one of */=>@|) to entries
      --file-type            likewise, except do not append '*'
      --format=WORD          across -x, commas -m, horizontal -x, long -l,
                               single-column -1, verbose -l, vertical -C
      --full-time            like -l --time-style=full-iso
  -g                         like -l, but do not list owner
      --group-directories-first
tryhackme@linux2:~$
This option is, in fact, a formatted output of what is called the man page (short for manual), which contains documentation for Linux commands and applications.

The Man(ual) Page

The manual pages are a great source of information for both system commands and applications available on both a Linux machine, which is accessible on the machine itself and online.

To access this documentation, we can use the man command and then provide the command we want to read the documentation for. Using our ls example, we would use man ls to view the manual pages for ls like so:

Listing the options we can use with ls
tryhackme@linux2:~$ man ls
LS(1)                                               User Commands                                               LS(1)

NAME
       ls - list directory contents

SYNOPSIS
       ls [OPTION]... [FILE]...

DESCRIPTION
       List  information  about the FILEs (the current directory by default).  Sort entries alphabetically if none of
       -cftuvSUX nor --sort is specified.

       Mandatory arguments to long options are mandatory for short options too.

       -a, --all
              do not ignore entries starting with .

       -A, --almost-all
              do not list implied . and ..

       --author
              with -l, print the author of each file

       -b, --escape
              print C-style escapes for nongraphic characters

       --block-size=SIZE
              with -l, scale sizes by SIZE when printing them; e.g., '--block-size=M'; see SIZE format below

 Manual page ls(1) line 1 (press h for help or q to quit)

 We covered some of the most fundamental commands when interacting with the filesystem on the Linux machine. For example, we covered how to list and find the contents of folders using ls and find and navigating the filesystem using cd. 

In this task, we're going to learn some more commands for interacting with the filesystem to allow us to:

create files and folders
move files and folders
delete files and folders
More specifically, the following commands:

Command	Full Name	Purpose
touch	touch	Create file
mkdir	make directory	Create a folder
cp	copy	Copy a file or folder
mv	move	Move a file or folder
rm	remove	Remove a file or folder
file	file	Determine the type of a file
Protip: Similarly to using cat, we can provide full file paths, i.e. directory1/directory2/note for all of these commands



Creating Files and Folders (touch, mkdir)

Creating files and folders on Linux is a simple process. First, we'll cover creating a file. The touch command takes exactly one argument -- the name we want to give the file we create. For example, we can create the file "note" by using touch note. It's worth noting that touch simply creates a blank file. You would need to use commands like echo or text editors such as nano to add content to the blank file.

Using touch to create a new file
tryhackme@linux2:~$ touch note
tryhackme@linux2:~$ ls           
folder1 note
This is a similar process for making a folder, which just involves using the mkdir command and again providing the name that we want to assign to the directory. For example, creating the directory "mydirectory" using mkdir mydirectory.

Creating a new directory with mkdir
tryhackme@linux2:~$ mkdir mydirectory
tryhackme@linux2:~$ ls           
folder1 mydirectory note


Removing Files and Folders (rm)

rm is extraordinary out of the commands that we've covered so far. You can simply remove files by using rm. However, you need to provide the -R switch alongside the name of the directory you wish to remove.

Using rm to remove a file
tryhackme@linux2:~$ rm note
tryhackme@linux2:~$ ls           
folder1 mydirectory
Using rm recursively to remove a directory
tryhackme@linux2:~$ rm -R mydirectory
tryhackme@linux2:~$ ls           
folder1


Copying and Moving Files and Folders (cp, mv)

Copying and moving files is an important functionality on a Linux machine. Starting with cp, this command takes two arguments:

1. the name of the existing file

2. the name we wish to assign to the new file when copying

cp copies the entire contents of the existing file into the new file. In the screenshot below, we are copying "note" to "note2".

Using cp to copy a file
tryhackme@linux2:~$ cp note note2
tryhackme@linux2:~$ ls           
folder1 note note2
Moving a file takes two arguments, just like the cp command. However, rather than copying and/or creating a new file, mv will merge or modify the second file that we provide as an argument. Not only can you use mv to move a file to a new folder, but you can also use mv to rename a file or folder. For example, in the screenshot below, we are renaming the file "note2" to be named "note3". "note3" will now have the contents of "note2". 

Using mv to move a file
tryhackme@linux2:~$ mv note2 note3
tryhackme@linux2:~$ ls           
folder1 note note3


Determining File Type

What is often misleading and often catches people out is making presumptions from files as to what their purpose or contents may be. Files usually have what's known as an extension to make this easier. For example, text files usually have an extension of ".txt". But this is not necessary.

So far, the files we have used in our examples haven't had an extension. Without knowing the context of why the file is there -- we don't really know its purpose. Enter the file command. This command takes one argument. For example, we'll use file to confirm whether or not the "note" file in our examples is indeed a text file, like so file note.

Using file to determine the contents of a file
tryhackme@linux2:~$ file note
note: ASCII text

As you would have already found out by now, certain users cannot access certain files or folders. We've previously explored some commands that can be used to determine what access we have and where it leads us. 

In our previous tasks, we learned how to extend the use of commands through flags and switches. Take, for example, the ls command, which lists the contents of the current directory. When using the -l switch, we can see ten columns such as in the screenshot below. However, we're only interested in the first three columns:

Using ls -lh to list the permissions of all files in the directory
tryhackme@linux2:~$ ls -lh
-rw-r--r-- 1 cmnatic cmnatic 0 Feb 19 10:37 file1
-rw-r--r-- 8 cmnatic cmnatic 0 Feb 19 10:37 file2
Although intimidating, these three columns are very important in determining certain characteristics of a file or folder and whether or not we have access to it. A file or folder can have a couple of characteristics that determine both what actions are allowed and what user or group has the ability to perform the given action -- such as the following:

Read
Write
Execute 
Using su to switch to user2

tryhackme@linux2:~$ su user2
Password:
user2@linux2:/home/tryhackme$
Let's use the "cmnatic.pem" file in our initial screenshot at the top of this task. It has the "-" indicator highlighting that it is a file and then "rw" followed after. This means that only the owner of the file can read and write to this"cmnatic.pem" file but cannot execute it.

Briefly: The Differences Between Users & Groups

We briefly explored this in Linux fundamentals part 1 (namely, the differences between a regular user and a system user). The great thing about Linux is that permissions can be so granular, that whilst a user technically owns a file, if the permissions have been set, then a group of users can also have either the same or a different set of permissions to the exact same file without affecting the file owner itself.

Let's put this into a real-world context; the system user that runs a web server must have permissions to read and write files for an effective web application. However, companies such as web hosting companies will have to want to allow their customers to upload their own files for their website without being the webserver system user -- compromising the security of every other customer. 

We'll learn the commands necessary to switch between users below.



Switching Between Users

Switching between users on a Linux install is easy work thanks to the su command. Unless you are the root user (or using root permissions through sudo), then you are required to know two things to facilitate this transition of user accounts:

The user we wish to switch to
The user's password
The su command takes a couple of switches that may be of relevance to you. For example, executing a command once you log in or specifying a specific shell to use. I encourage you to read the man page for su to find out more. However, I will cover the -l or --login switch.

Simply, by providing the -l switch to su, we start a shell that is much more similar to the actual user logging into the system - we inherit a lot more properties of the new user, i.e., environment variables and the likes. 

Using su to switch to user2 interactively
tryhackme@linux2:~$ su user2
Password:
user2@linux2:/home/tryhackme$
For example, when using su to switch to "user2", our new session drops us into our previous user's home directory. 

Using su to switch to user2 interactively
tryhackme@linux2:~$ su -l user2
Password:
user2@linux2:~$ pwd
user2@:/home/user2$
Where now, after using -l, our new session has dropped us into the home directory of "user" automatically. 

/etc

This root directory is one of the most important root directories on your system. The etc folder (short for etcetera) is a commonplace location to store system files that are used by your operating system. 

For example, the sudoers file highlighted in the screenshot below contains a list of the users & groups that have permission to run sudo or a set of commands as the root user.

Also highlighted below are the "passwd" and "shadow" files. These two files are special for Linux as they show how your system stores the passwords for each user in encrypted formatting called sha512.

Some notable contents of the /etc directory
tryhackme@linux2:/etc$ ls
shadow passwd sudoers sudoers.d


/var

The "/var" directory, with "var" being short for variable data,  is one of the main root folders found on a Linux install. This folder stores data that is frequently accessed or written by services or applications running on the system. For example, log files from running services and applications are written here (/var/log), or other data that is not necessarily associated with a specific user (i.e., databases and the like).

Some notable contents of the /var directory
tryhackme@linux2:/var$ ls
backups log opt tmp


/root

Unlike the /home directory, the /root folder is actually the home for the "root" system user. There isn't anything more to this folder other than just understanding that this is the home directory for the "root" user. But, it is worth a mention as the logical presumption is that this user would have their data in a directory such as "/home/root" by default.  

Some notable contents of the /root directory
root@linux2:~# ls
myfile myfolder passwords.xlsx


/tmp

This is a unique root directory found on a Linux install. Short for "temporary", the /tmp directory is volatile and is used to store data that is only needed to be accessed once or twice. Similar to the memory on your computer, once the computer is restarted, the contents of this folder are cleared out.

What's useful for us in pentesting is that any user can write to this folder by default. Meaning once we have access to a machine, it serves as a good place to store things like our enumeration scripts.

Some notable contents of the /tmp directory
root@linux2:/tmp# ls
todelete trash.txt rubbish.bin

Nice work! This room was quite theory-heavy and covered quite a range of the fundamentals in getting you familiar with Linux. To quickly recap, this room taught you:

How to connect to a Linux machine remotely using SSH
Advancing your use of commands by providing flags, switches and where you can go to learn about these for each command (man pages)
Some more commands that you'll frequently be using to interact with the filesystem and its contents
A brief introduction to file permissions & switching users
A summary paragraph of the important root directories on a Ubuntu Linux install and how we may be able to use the data stored within these.
I encourage you to go through this room again once or twice to gain some familiarity with the concepts. After all, practice makes perfect! 

Welcome to part three (and the finale) of the Linux Fundamentals module. So far, throughout the series, you have got hands-on with some fundamental concepts and used some important commands. This room is going to showcase some useful utilities and applications that you are likely to use day-to-day. You're also going to advance your Linux-fu skills by learning about automation, package management, and service/application logging. 

Throughout the series so far, we have only stored text in files using a combination of the echo command and the pipe operators (> and >>). This isn't an efficient way to handle data when you're working with files with multiple lines and the sorts!



Introducing terminal text editors

There are a few options that you can use, all with a variety of friendliness and utility. This task is going to introduce you to nano but also show you an alternative named VIM (which TryHackMe has a room dedicated to!)



Nano

It is easy to get started with Nano! To create or edit a file using nano, we simply use nano filename -- replacing "filename" with the name of the file you wish to edit.

Introducing Nano
tryhackme@linux3:/tmp# nano myfile
  GNU nano 4.8                                             myfile                                                       

^G Get Help    ^O Write Out   ^W Where Is    ^K Cut Text    ^J Justify     ^C Cur Pos     M-U Undo       M-A Mark Text
^X Exit        ^R Read File   ^\ Replace     ^U Paste Text  ^T To Spell    ^_ Go To Line  M-E Redo       M-6 Copy Text
Once we press enter to execute the command, nano will launch! Where we can just begin to start entering or modifying our text. You can navigate each line using the "up" and "down" arrow keys or start a new line using the "Enter" key on your keyboard.

Using Nano to write text
tryhackme@linux3:/tmp# nano myfile
  GNU nano 4.8                                             myfile                                             Modified  

Hello TryHackMe
I can write things into "myfile"


^G Get Help    ^O Write Out   ^W Where Is    ^K Cut Text    ^J Justify     ^C Cur Pos     M-U Undo       M-A Mark Text
^X Exit        ^R Read File   ^\ Replace     ^U Paste Text  ^T To Spell    ^_ Go To Line  M-E Redo       M-6 Copy Text
Nano has a few features that are easy to remember & covers the most general things you would want out of a text editor, including:

Searching for text
Copying and Pasting
Jumping to a line number
Finding out what line number you are on
You can use these features of nano by pressing the "Ctrl" key (which is represented as an ^ on Linux)  and a corresponding letter. For example, to exit, we would want to press "Ctrl" and "X" to exit Nano.



VIM

VIM is a much more advanced text editor. Whilst you're not expected to know all advanced features, it's helpful to mention it for powering up your Linux skills.



Some of VIM's benefits, albeit taking a much longer time to become familiar with, includes:

Customisable - you can modify the keyboard shortcuts to be of your choosing
Syntax Highlighting - this is useful if you are writing or maintaining code, making it a popular choice for software developers
VIM works on all terminals where nano may not be installed
There are a lot of resources such as cheatsheets, tutorials, and the sorts available to you use.
TryHackMe has a room showcasing VIM if you wish to learn more about this editor!

Downloading Files (Wget)

A pretty fundamental feature of computing is the ability to transfer files. For example, you may want to download a program, a script, or even a picture. Thankfully for us, there are multiple ways in which we can retrieve these files.

 We're going to cover the use of wget .  This command allows us to download files from the web via HTTP -- as if you were accessing the file in your browser. We simply need to provide the address of the resource that we wish to download. For example, if I wanted to download a file named "myfile.txt" onto my machine, assuming I knew the web address it -- it would look something like this:

wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt



Transferring Files From Your Host - SCP (SSH)

Secure copy, or SCP, is just that -- a means of securely copying files. Unlike the regular cp command, this command allows you to transfer files between two computers using the SSH protocol to provide both authentication and encryption.

Working on a model of SOURCE and DESTINATION, SCP allows you to:

Copy files & directories from your current system to a remote system
Copy files & directories from a remote system to your current system
Provided that we know usernames and passwords for a user on your current system and a user on the remote system. For example, let's copy an example file from our machine to a remote machine, which I have neatly laid out in the table below:

Variable	Value
The IP address of the remote system 	192.168.1.30
User on the remote system	ubuntu
Name of the file on the local system	important.txt
Name that we wish to store the file as on the remote system	transferred.txt
With this information, let's craft our scp command (remembering that the format of SCP is just SOURCE and DESTINATION)

scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt

And now let's reverse this and layout the syntax for using scp to copy a file from a remote computer that we're not logged into 

Variable	Value
IP address of the remote system	192.168.1.30
User on the remote system	ubuntu
Name of the file on the remote system	documents.txt
Name that we wish to store the file as on our system	notes.txt
The command will now look like the following: scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt 


Serving Files From Your Host - WEB

Ubuntu machines come pre-packaged with python3. Python helpfully provides a lightweight and easy-to-use module called "HTTPServer". This module turns your computer into a quick and easy web server that you can use to serve your own files, where they can then be downloaded by another computing using commands such as curl and wget. 

Python3's "HTTPServer" will serve the files in the directory where you run the command, but this can be changed by providing options that can be found within the manual pages. Simply, all we need to do is run python3 -m  http.server in the terminal to start the module! In the snippet below, we are serving from a directory called "webserver", which has a single named "file".

Using Python to start a web server
tryhackme@linux3:/webserver# python3 -m http.server
Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
Now, let's use wget to download the file using the MACHINE_IP address and the name of the file. Remember, because the python3 server is running port 8000, you will need to specify this within your wget command. For example:

An example wget command of a web server running on port 8000
tryhackme@mymachine:~# wget http://MACHINE_IP:8000/myfile
Note, you will need to open a new terminal to use wget and leave the one that you have started the Python3 web server in. This is because, once you start the Python3 web server, it will run in that terminal until you cancel it.

Let's take a look in the snippet below as an example:
Downloading a file from our webserver using wget
tryhackme@linux3:/tmp# wget http://MACHINE_IP:8000/file

2021-05-04 14:26:16  http://127.0.0.1:8000/file
Connecting to http://127.0.0.1:8000... connected.
HTTP request sent, awaiting response... 200 OK
Length: 51095 (50K) [text]
Saving to: ‘file’

file                    100%[=================================================>]  49.90K  --.-KB/s    in 0.04s

2021-05-04 14:26:16 (1.31 MB/s) - ‘file’ saved [51095/51095]
Remember, you will need to run the wget command in another terminal (while keeping the terminal that is running the Python3 server active). An example of this on the TryHackMe AttackBox is below:



One flaw with this module is that you have no way of indexing, so you must know the exact name and location of the file that you wish to use. This is why I prefer to use Updog. What's Updog? A more advanced yet lightweight webserver. But for now, let's stick to using Python's "HTTP Server".

Processes are the programs that are running on your machine. They are managed by the kernel, where each process will have an ID associated with it, also known as its PID. The PID increments for the order In which the process starts. I.e. the 60th process will have a PID of 60.

Viewing Processes

We can use the friendly ps command to provide a list of the running processes as our user's session and some additional information such as its status code, the session that is running it, how much usage time of the CPU it is using, and the name of the actual program or command that is being executed:



Note how in the screenshot above, the second process ps has a PID of 204, and then in the command below it, this is then incremented to 205.

To see the processes run by other users and those that don't run from a session (i.e. system processes), we need to provide aux to the ps command like so: ps aux



Note we can see a total of 5 processes -- note how we now have "root"  and "cmnatic"

Another very useful command is the top command; top gives you real-time statistics about the processes running on your system instead of a one-time view. These statistics will refresh every 10 seconds, but will also refresh when you use the arrow keys to browse the various rows. Another great command to gain insight into your system is via the top command



Managing Processes

You can send signals that terminate processes; there are a variety of types of signals that correlate to exactly how "cleanly" the process is dealt with by the kernel. To kill a command, we can use the appropriately named kill command and the associated PID that we wish to kill. i.e., to kill PID 1337, we'd use kill 1337.

Below are some of the signals that we can send to a process when it is killed:

SIGTERM - Kill the process, but allow it to do some cleanup tasks beforehand
SIGKILL - Kill the process - doesn't do any cleanup after the fact
SIGSTOP - Stop/suspend a process


How do Processes Start?

Let's start off by talking about namespaces. The Operating System (OS) uses namespaces to ultimately split up the resources available on the computer to (such as CPU, RAM and priority) processes. Think of it as splitting your computer up into slices -- similar to a cake. Processes within that slice will have access to a certain amount of computing power, however, it will be a small portion of what is actually available to every process overall.

Namespaces are great for security as it is a way of isolating processes from another -- only those that are in the same namespace will be able to see each other.

We previously talked about how PID works, and this is where it comes into play. The process with an ID of 0 is a process that is started when the system boots. This process is the system's init on Ubuntu, such as systemd, which is used to provide a way of managing a user's processes and sits in between the operating system and the user. 

For example, once a system boots and it initialises, systemd is one of the first processes that are started. Any program or piece of software that we want to start will start as what's known as a child process of systemd. This means that it is controlled by systemd, but will run as its own process (although sharing the resources from systemd) to make it easier for us to identify and the likes.





 Getting Processes/Services to Start on Boot

Some applications can be started on the boot of the system that we own. For example, web servers, database servers or file transfer servers. This software is often critical and is often told to start during the boot-up of the system by administrators.

In this example, we're going to be telling the apache web server to be starting apache manually and then telling the system to launch apache2 on boot.

Enter the use of systemctl -- this command allows us to interact with the systemd process/daemon. Continuing on with our example, systemctl is an easy to use command that takes the following formatting: systemctl [option] [service]

For example, to tell apache to start up, we'll use systemctl start apache2. Seems simple enough, right? Same with if we wanted to stop apache, we'd just replace the [option] with stop (instead of start like we provided)

We can do four options with systemctl:

Start
Stop
Enable
Disable
An Introduction to Backgrounding and Foregrounding in Linux

Processes can run in two states: In the background and in the foreground. For example, commands that you run in your terminal such as "echo" or things of that sort will run in the foreground of your terminal as it is the only command provided that hasn't been told to run in the background. "Echo" is a great example as the output of echo will return to you in the foreground, but wouldn't in the background - take the screenshot below, for example.



Here we're running echo "Hi THM" , where we expect the output to be returned to us like it is at the start. But after adding the & operator to the command, we're instead just given the ID of the echo process rather than the actual output -- as it is running in the background.

This is great for commands such as copying files because it means that we can run the command in the background and continue on with whatever further commands we wish to execute (without having to wait for the file copy to finish first)

We can do the exact same when executing things like scripts -- rather than relying on the & operator, we can use Ctrl + Z on our keyboard to background a process. It is also an effective way of "pausing" the execution of a script or command like in the example below:



This script will keep on repeating "This will keep on looping until I stop!" until I stop or suspend the process. By using Ctrl + Z (as indicated by T^Z). Now our terminal is no longer filled up with messages -- until we foreground it, which we will discuss below.



Foregrounding a process

Now that we have a process running in the background, for example, our script "background.sh" which can be confirmed by using the ps aux command, we can back-pedal and bring this process back to the foreground to interact with.



With our process backgrounded using either Ctrl + Z or the & operator, we can use fg to bring this back to focus like below, where we can see the fg command is being used to bring the background process back into use on the terminal, where the output of the script is now returned to us.




Users may want to schedule a certain action or task to take place after the system has booted. Take, for example, running commands, backing up files, or launching your favourite programs on, such as Spotify or Google Chrome.

We're going to be talking about the cron process, but more specifically, how we can interact with it via the use of crontabs . Crontab is one of the processes that is started during boot, which is responsible for facilitating and managing cron jobs.



A crontab is simply a special file with formatting that is recognised by the cron process to execute each line step-by-step. Crontabs require 6 specific values:

Value	Description
MIN	What minute to execute at
HOUR	What hour to execute at
DOM	What day of the month to execute at
MON	What month of the year to execute at
DOW	What day of the week to execute at
CMD	The actual command that will be executed.


Let's use the example of backing up files. You may wish to backup "cmnatic"'s  "Documents" every 12 hours. We would use the following formatting: 

0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/

An interesting feature of crontabs is that these also support the wildcard or asterisk (*). If we do not wish to provide a value for that specific field, i.e. we don't care what month, day, or year it is executed -- only that it is executed every 12 hours, we simply just place an asterisk.

This can be confusing to begin with, which is why there are some great resources such as the online "Crontab Generator" that allows you to use a friendly application to generate your formatting for you! As well as the site "Cron Guru"!

Crontabs can be edited by using crontab -e, where you can select an editor (such as Nano) to edit your crontab.



Introducing Packages & Software Repos

When developers wish to submit software to the community, they will submit it to an  "apt" repository. If approved, their programs and tools will be released into the wild. Two of the most redeeming features of Linux shine to light here: User accessibility and the merit of open source tools.

When using the ls command on a Ubuntu 20.04 Linux machine, these files serve as the gateway/registry. 





Whilst Operating System vendors will maintain their own repositories, you can also add community repositories to your list! This allows you to extend the capabilities of your OS. Additional repositories can be added by using the add-apt-repositorycommand or by listing another provider! For example, some vendors will have a repository that is closer to their geographical location.



Managing Your Repositories (Adding and Removing)

Normally we use the apt command to install software onto our Ubuntu system. The apt command is a part of the package management software also named apt. Apt contains a whole suite of tools that allows us to manage the packages and sources of our software, and to install or remove software at the same time.

One method of adding repositories is to use the add-apt-repository command we illustrated above, but we're going to walk through adding and removing a repository manually. Whilst you can install software through the use of package installers such as dpkg, the benefits of apt means that whenever we update our system -- the repository that contains the pieces of software that we add also gets checked for updates. 

In this example, we're going to add the text editor Sublime Text to our Ubuntu machine as a repository as it is not a part of the default Ubuntu repositories. When adding software, the integrity of what we download is guaranteed by the use of what is called GPG (Gnu Privacy Guard) keys. These keys are essentially a safety check from the developers saying, "here's our software". If the keys do not match up to what your system trusts and what the developers used, then the software will not be downloaded.

So, to start, we need to add the GPG key for the developers of Sublime Text 3. (Note that TryHackMe instances do not have internet access and so we're not expecting you to add this to the machine that you deploy, as it would fail.)

1. Let's download the GPG key and use apt-key to trust it:  wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -

2. Now that we have added this key to our trusted list, we can now add Sublime Text 3's repository to our apt sources list. A good practice is to have a separate file for every different community/3rd party repository that we add.

2.1. Let's create a file named sublime-text.list in /etc/apt/sources.list.d and enter the repository information like so:



2.2. And now use Nano or a text editor of your choice to add & save the Sublime Text 3 repository into this newly created file:



2.3. After we have added this entry, we need to update apt to recognise this new entry -- this is done using the apt update command

2.4. Once successfully updated, we can now proceed to install the software that we have trusted and added to apt using apt install sublime-text

Removing packages is as easy as reversing. This process is done by using the add-apt-repository --remove ppa:PPA_Name/ppa command or by manually deleting the file that we previously added to. Once removed, we can just use apt remove [software-name-here] i.e. apt remove sublime-text

We briefly touched upon log files and where they can be found in Linux Fundamentals Part 1. However, let's quickly recap. Located in the /var/log directory, these files and folders contain logging information for applications and services running on your system. The Operating System  (OS) has become pretty good at automatically managing these logs in a process that is known as "rotating".

I have highlighted some logs from three services running on a Ubuntu machine:

An Apache2 web server
Logs for the fail2ban service, which is used to monitor attempted brute forces, for example
The UFW service which is used as a firewall


These services and logs are a great way in monitoring the health of your system and protecting it. Not only that, but the logs for services such as a web server contain information about every single request - allowing developers or administrators to diagnose performance issues or investigate an intruder's activity. For example, the two types of log files below that are of interest:

access log
error log


There are, of course, logs that store information about how the OS is running itself and actions that are performed by users, such as authentication attempts.

Welcome to the end of the Linux Fundamentals module. Your familiarity with Linux will improve as you get to interact with it over time. Linux has the potential to do very powerful things with relative ease (as you have hopefully discovered throughout this module)

To recap, this room introduced you to the following topics:

Using terminal text editors
General utilities such as downloading and serving contents using a python webserver
A look into processes
Maintaining & automating your system by the use of crontabs, package management, and reviewing logs
Continue your learning in some other TryHackMe rooms that are dedicated to Linux tools or utilities:

Bash Scripting - https://tryhackme.com/room/bashscripting
Regular Expressions - https://tryhackme.com/room/catregex