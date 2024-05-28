# Glastopf Honeypot Server
## Glastopf Honeypot server 

### What is the Glastopf honeypot server?

The Glastopf honeypot server is a web application designed to act as a honeypot for researchers, security professionals, and individuals interested in security research. 

**Key features:**

* **Simulates 100 different services and ports** to attract attackers while minimizing risk. 
* **Log and analyze attacker techniques**, providing valuable data for researchers. 
* **Modular and easy to customize**, allowing users to add new honeypots or services.
* **Runs on affordable and secure hardware**, like Raspberry Pi and Debian Linux.

### How it works

Glastopf runs as a web application on Apache, offering various network services over different ports. When an attacker tries to interact with these services, Glastopf logs the interaction, capturing information such as:

* Attacker IP address
* Date and time of the attack
* Service the attacker targeted
* Any data the attacker sent
* Any files the attacker downloaded

This information provides researchers and security professionals valuable insights into attacker techniques and behaviors. 

### Benefits of using Glastopf

* **Identify and analyze attack trends:** Glastopf helps security professionals understand how attackers operate, allowing them to better protect their networks.
* **Gather intelligence on malware and exploits:** By logging and analyzing attacker actions, Glastopf can identify new malware and exploits before they cause widespread damage.
* **Educate the security community:** Glastopf helps security researchers share information about attack techniques, leading to improved detection and prevention methods.
* **Learn about network security:** Individuals interested in security research can use Glastopf to gain hands-on experience with attacker behavior.

### Installation and usage

To set up Glastopf, you need a Raspberry Pi and an SD card. Download the latest image from the Glastopf website and install it on your SD card. 

Once installed, you can configure the honeypot and launch it. The web interface provides access to various features and functionalities, including:

* **Viewing live logs of attacker activity.**
* **Downloading archived logs for analysis.**
* **Adding new honey pots and services.**
* **Analyzing attacker trends and behaviors.**


### Documentation and resources

Glastopf offers comprehensive documentation and resources to get you started:

* **Documentation:** https://glastopf.com/
* **Repository:** https://github.com/glastopf/glastopf
* **Tutorials:** https://glastopf.com/docs/tutorials/
* **FAQs:** https://glastopf.com/docs/faq/


By providing a safe environment for observing attacker behavior, Glastopf is a valuable tool for security researchers, professionals, and enthusiasts who want to understand and combat cyberattacks.
