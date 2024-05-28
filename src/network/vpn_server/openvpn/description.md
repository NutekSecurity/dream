# OpenVPN VPN Server
## OpenVPN Server Setup

Setting up your own OpenVPN server can be a great way to secure your internet connection and access resources remotely. Here's a detailed guide to help you get started:

### Requirements:

* A server running Linux (Ubuntu is recommended)
* A static IP address for the server
* Root access to the server
* OpenVPN client on the devices you want to connect

### Installation:

1. **Update your system:**

```bash
sudo apt update
sudo apt upgrade
```

2. **Install OpenVPN:**

```bash
sudo apt install openvpn
```

3. **Download Easy-RSA for certificate management:**

```bash
git clone https://github.com/OpenVPN/easy-rsa.git
```

4. **Configure Easy-RSA:**

```bash
cd easy-rsa
./easyrsa init-pki
./easyrsa build-ca nopass
./easyrsa gen-dh
./easyrsa build-server-full server nopass
./easyrsa build-client-full client1 nopass
```

5. **Copy certificates and keys:**

```bash
cp pki/ca.crt /etc/openvpn/
cp pki/issued/server.crt /etc/openvpn/
cp pki/private/server.key /etc/openvpn/
cp pki/dh.pem /etc/openvpn/
cp pki/issued/client1.crt /etc/openvpn/
cp pki/private/client1.key /etc/openvpn/
```

6. **Create OpenVPN configuration file:**

```bash
nano /etc/openvpn/server.conf
```

Paste the following configuration, making changes where appropriate:

```
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push \"redirect-gateway def1 bypass-dhcp\"
push \"dhcp-option DNS 8.8.8.8\"
push \"dhcp-option DNS 8.8.4.4\"
push \"route-method exe\"
keepalive 10 120
comp-lzo 
user nobody
group nogroup
persist-key
persist-tun
status /var/log/openvpn/server-status.log
log-append /var/log/openvpn/server.log
verb 3
```

7. **Enable IP forwarding and NAT:**

```bash
sudo echo 1 \u003e /proc/sys/net/ipv4/ip_forward
sudo iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -j MASQUERADE
sudo netfilter-persistent save
```

8. **Start OpenVPN:**

```bash
sudo systemctl start openvpn
sudo systemctl enable openvpn
```

9. **Connect from a client:**

1. Import `client1.crt` and `client1.key` to your OpenVPN client.
2. Configure the client with the following parameters:
 - Server address: your server's IP address
 - Port: 1194
 - Protocol: UDP
 - CA certificate: ca.crt

### Additional Notes:

* This guide is a basic example. You may need to adjust the configuration depending on your specific needs.
* For security reasons, it's important to keep OpenVPN updated and use strong passwords for your certificates and keys.
* You can find additional information and resources on the OpenVPN website: https://openvpn.net/

## Further Resources:

* DigitalOcean tutorial: https://www.digitalocean.com/community/tutorials/how-to-set-up-and-configure-an-openvpn-server-on-ubuntu-20-04
* Linuxize tutorial: https://linuxize.com/post/how-to-install-and-configure-openvpn-on-ubuntu-22-04/
* OpenVPN documentation: https://openvpn.net/index.php/access-server/docs/

I hope this helps! Let me know if you have any other questions.
