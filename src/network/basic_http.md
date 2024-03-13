# Basic HTTP

Hypertext Transfer Protocol (HTTP) is the protocol used to transfer web pages. Your web browser connects to the webserver and uses HTTP to request HTML pages and images among other files and submit forms and upload various files. Anytime you browse the World Wide Web (WWW), you are certainly using the HTTP protocol.

The image below shows a client requesting the HTML page index.html, which the webserver provides. Then the client requests an image, logo.jpg, and the web server sends it.



HTTP sends and receives data as cleartext (not encrypted); therefore, you can use a simple tool, such as Telnet (or Netcat), to communicate with a web server and act as a “web browser”. The key difference is that you need to input the HTTP-related commands instead of the web browser doing that for you.

In the following example, we will see how we can request a page from a web server; moreover, we will discover the webserver version. To accomplish this, we will use the Telnet client. We chose it because Telnet is a simple protocol; furthermore, it uses cleartext for communication. We will use telnet instead of a web browser to request a file from the webserver. The steps will be as follows:

First, we connect to port 80 using telnet 10.10.176.214 80.
Next, we need to type GET /index.html HTTP/1.1 to retrieve the page index.html or GET / HTTP/1.1 to retrieve the default page.
Finally, you need to provide some value for the host like host: telnet and hit the Enter/Return key twice.
In the console output below, we could recover the requested page along with a trove of information not usually displayed by the web browser. If the page we requested is not found, we get error 404.

Pentester Terminal
pentester@TryHackMe$ telnet 10.10.176.214 80
Trying 10.10.176.214...
Connected to MACHINE_IP.
Escape character is '^]'.
GET /index.html HTTP/1.1
host: telnet

HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
Date: Wed, 15 Sep 2021 08:56:20 GMT
Content-Type: text/html
Content-Length: 234
Last-Modified: Wed, 15 Sep 2021 08:53:59 GMT
Connection: keep-alive
ETag: "6141b4a7-ea"
Accept-Ranges: bytes

<!DOCTYPE html>
<html lang="en">
<head>
  <title>Welcome to my Web Server</title>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
</head>
<body>
  <h1>Coming Soon<h1>
</body>
</html>
Of particular interest in the output above is that the user needs only to type a couple of commands to get the page they need: GET /index.html HTTP/1.1 followed by host: telnet.

We need an HTTP server (webserver) and an HTTP client (web browser) to use the HTTP protocol. The web server will “serve” a specific set of files to the requesting web browser.

Three popular choices for HTTP servers are:

Apache
Internet Information Services (IIS)
nginx
Apache and Nginx are free and open-source software. However, IIS is closed source software and requires paying for a license.

There are many web browsers available. At the time of writing, the most popular web browsers are:

Chrome by Google
Edge by Microsoft
Firefox by Mozilla
Safari by Apple.
Web browsers are generally free to install and use; furthermore, tech giants battle for a higher market share for their browsers.