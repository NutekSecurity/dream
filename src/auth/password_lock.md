# Username enumeration via account lock

## Using ffuf to brute force username and password when account lockout is in place

<a href="https://asciinema.org/a/DPfKPWmuZq5TjLdYJSVMTFJJ3" target="_blank"><img src="https://asciinema.org/a/DPfKPWmuZq5TjLdYJSVMTFJJ3.svg" /></a>

Few times run below command to get the username that the response size is different than 3132, that is the username that exists

```shell
ffuf -X POST -replay-proxy http://0.0.0.0:8088  -u https://0a2f0039041fb2658d054ce400c5005a.web-security-academy.net/login -w auth-lock/auth-lock-usernames -fs 3132 -d "username=FUZZ&password=example"
```

Run this command to get user password from above command

```shell
ffuf -X POST -replay-proxy http://0.0.0.0:8088 -u https://0a2f0039041fb2658d054ce400c5005a.web-security-academy.net/login -w auth-lock/auth-lock-passwords -fs 3184 -d "username=ae&password=FUZZ"
```

Now we need to wait 1 minute, to account lock expire...

Congratulations, we solved another lab!

Sure. The Username enumeration via account lock tutorial example in PortSwigger Academy demonstrates how a website can be vulnerable to username enumeration attacks.

In the tutorial, the user is first prompted to enter their username and password. After they have successfully entered their credentials, they are logged in to the website.

The website has a mechanism in place to prevent users from guessing usernames. This mechanism locks the account for a period of time if the user enters an invalid username three times.

However, the username enumeration attack works by exploiting this mechanism. Specifically, the attacker can submit a list of usernames to the website and wait for the accounts to be locked.

Once the accounts are locked, the attacker can then try to log in to the website using the locked accounts. If the attacker is lucky, they will be able to log in to one of the accounts and gain access to the website.

To exploit this vulnerability, the attacker would first need to obtain a list of possible usernames for the website. This could be done through a variety of methods, such as social engineering or dictionary attacks.

Once the attacker has a list of possible usernames, they would need to submit the list to the website and wait for the accounts to be locked. Once the accounts are locked, the attacker can then try to log in to the website using the locked accounts. If the attacker is lucky, they will be able to log in to one of the accounts and gain access to the website.

The Username enumeration via account lock tutorial example is a good demonstration of how a website can be vulnerable to username enumeration attacks. It is important to be aware of these vulnerabilities and to take steps to protect yourself.

Here are some tips for protecting yourself from username enumeration attacks:

* Use a strong username for your online accounts.
* Change your usernames regularly.
* Be suspicious of emails or text messages that ask for your personal information.
* Install antivirus software and keep it up to date.
* Be careful about what websites you visit and what links you click on.
* Train yourself and your employees on how to identify and avoid phishing attacks.

By following these tips, you can help to protect yourself from username enumeration attacks and keep your accounts safe.

In addition to the tips above, there are a few things that the website can do to protect itself from username enumeration attacks:

* Implement a rate limiting mechanism to prevent users from submitting too many requests in a short period of time.
* Use a honeypot account to lure attackers into entering invalid usernames.
* Implement a CAPTCHA challenge to verify that the user is human.
* Monitor the website for suspicious activity, such as a large number of failed login attempts.

By implementing these measures, the website can help to protect itself from username enumeration attacks.