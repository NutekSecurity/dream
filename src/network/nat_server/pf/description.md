# pf NAT Server
## Port Forwarding using Network Address Translation (NAT)

## What is Port Forwarding

Port forwarding is used to allow incoming connections on a specific network port to be directed to a specific device on a private network. In simpler terms, port forwarding creates a tunnel from the public internet to an internal device on a private network, typically behind a router and NAT firewall. This is necessary because a NAT firewall only allows outbound connections by default, preventing external devices from initiating connections to internal devices.

## NAT

Network Address Translation (NAT) enables multiple devices on a private network to share a single public IP address, allowing them to communicate with the internet. However, NAT also introduces a layer of security, as external devices cannot directly access internal devices on the local network.

## Setting up Port Forwarding on a NAT Router

Here are the specific steps on how to set up port forwarding on a NAT router:

**1. Access the Router Interface:**
- Log in to the router's web interface using a web browser. The router's web address and login credentials can be found in its user manual.
- Alternatively, you might be able to access the router interface through a mobile app, though the interface options might be limited.

**2. Find the Port Forwarding Section:**
- The location of the Port Forwarding setting varies across router models but is typically found under sections labeled \"Port Forwarding,\" \"NAT\", \"Virtual Servers,\" \"Gaming,\" or a similar variation.

**3. Create a New Rule:**
- Click on the option to add a new port forwarding rule.
- Enter the following information:
 LICENSE README.md go.mod go.sum lol.rb main.go prompt-response prompt-subject run-prompt-subject.rb **Service Name:** A name for the rule (e.g., \"Gaming PC\")
 LICENSE README.md go.mod go.sum lol.rb main.go prompt-response prompt-subject run-prompt-subject.rb **Protocol:** The type of traffic (e.g., TCP, UDP) used by the application.
 LICENSE README.md go.mod go.sum lol.rb main.go prompt-response prompt-subject run-prompt-subject.rb **External Port:** The port number that will be used on the public internet.
 LICENSE README.md go.mod go.sum lol.rb main.go prompt-response prompt-subject run-prompt-subject.rb **Internal Port:** The port number used by the application on the internal device. This might be the same as the external port or different depending on the application's configuration.
 LICENSE README.md go.mod go.sum lol.rb main.go prompt-response prompt-subject run-prompt-subject.rb **Internal IP Address:** The private IP address of the device that you want to access from the internet. You can usually find the IP address of the device in its network settings or through the DHCP client list in the router interface.

**4. Save and Enable the Rule.**
- Click \"Save,\" \"Apply,\" or a similar option to activate the port forwarding rule.
- Ensure that the rule you created is enabled and not disabled.

## Additional Notes:

* Some applications require specific port ranges to function properly. In such cases, you will need to forward the entire range of ports instead of a single port.
* If you encounter difficulties setting up port forwarding, consult your router’s user manual or contact your internet service provider for assistance.
* It’s important to only forward the ports that are needed for specific applications or services, and to disable port forwarding when not in use. This helps improve the security of your network.
* Be aware that port forwarding can introduce security vulnerabilities if not implemented correctly. Ensure you have adequate security measures in place on the device you are forwarding ports to.


## Resources

* Wikipedia: https://en.wikipedia.org/wiki/Port_forwarding
* How to Set Up Port Forwarding: https://helpdesk.flexiple.com/en/articles/4961708-how-to-set-up-port-forwarding
* Network address translation: https://en.wikipedia.org/wiki/Network_address_translation
