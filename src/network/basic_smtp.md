# Basic SMTP

Email is one of the most used services on the Internet. There are various configurations for email servers; for instance, you may set up an email system to allow local users to exchange emails with each other with no access to the Internet. However, we will consider the more general setup where different email servers connect over the Internet.

Email delivery over the Internet requires the following components:

Mail Submission Agent (MSA)
Mail Transfer Agent (MTA)
Mail Delivery Agent (MDA)
Mail User Agent (MUA)
The above four terms may look cryptic, but they are more straightforward than they appear. We will explain these terms using the figure below.



The figure shows the following five steps that an email needs to go through to reach the recipient’s inbox:

A Mail User Agent (MUA), or simply an email client, has an email message to be sent. The MUA connects to a Mail Submission Agent (MSA) to send its message.
The MSA receives the message, checks for any errors before transferring it to the Mail Transfer Agent (MTA) server, commonly hosted on the same server.
The MTA will send the email message to the MTA of the recipient. The MTA can also function as a Mail Submission Agent (MSA).
A typical setup would have the MTA server also functioning as a Mail Delivery Agent (MDA).
The recipient will collect its email from the MDA using their email client.
If the above steps sound confusing, consider the following analogy:

You (MUA) want to send postal mail.
The post office employee (MSA) checks the postal mail for any issues before your local post office (MTA) accepts it.
The local post office checks the mail destination and sends it to the post office (MTA) in the correct country.
The post office (MTA) delivers the mail to the recipient mailbox (MDA).
The recipient (MUA) regularly checks the mailbox for new mail. They notice the new mail, and they take it.
In the same way, we need to follow a protocol to communicate with an HTTP server, and we need to rely on email protocols to talk with an MTA and an MDA. The protocols are:

Simple Mail Transfer Protocol (SMTP)
Post Office Protocol version 3 (POP3) or Internet Message Access Protocol (IMAP)
We explain SMTP in this task and elaborate on POP3 and IMAP in the following two tasks.

Simple Mail Transfer Protocol (SMTP) is used to communicate with an MTA server. Because SMTP uses cleartext, where all commands are sent without encryption, we can use a basic Telnet client to connect to an SMTP server and act as an email client (MUA) sending a message.

SMTP server listens on port 25 by default. To see basic communication with an SMTP server, we used Telnet to connect to it. Once connected, we issue helo hostname and then start typing our email.

Pentester Terminal
pentester@TryHackMe$ telnet 10.10.176.214 25
Trying 10.10.176.214...
Connected to MACHINE_IP.
Escape character is '^]'.
220 bento.localdomain ESMTP Postfix (Ubuntu)
helo telnet
250 bento.localdomain
mail from: 
250 2.1.0 Ok
rcpt to: 
250 2.1.5 Ok
data
354 End data with .
subject: Sending email with Telnet
Hello Frank,
I am just writing to say hi!             
.
250 2.0.0 Ok: queued as C3E7F45F06
quit
221 2.0.0 Bye
Connection closed by foreign host.
After helo, we issue mail from:, rcpt to: to indicate the sender and the recipient. When we send our email message, we issue the command data and type our message. We issue <CR><LF>.<CR><LF> (or Enter . Enter to put it in simpler terms). The SMTP server now queues the message.

Generally speaking, we don’t need to memorize SMTP commands. The console output above aims to help better explain what a typical mail client does when it uses SMTP.