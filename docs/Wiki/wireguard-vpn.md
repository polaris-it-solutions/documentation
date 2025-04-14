---
title: Wireguard VPN
description: Wireguard VPN
published: true
date: 2024-10-08T08:45:57.709Z
tags: 
editor: markdown
dateCreated: 2024-10-08T08:45:57.709Z
---

# Introduction

Wireguard VPN is used for clients who need to access websites that are geo-locked. Currently Polaris Solutions IT Consultancy has 2 VPN servers. One terminating in Australia, and one terminating in Singapore. Initial plan was to have all staff using Wireguard VPN to protect data and add anonymity. Future plan is to transition to Secure DNS, hosted in Singapore. The Australia VPN service will remain for those staff who need access to Austraila based geo-blocked websites.

# Server Installation

## Overview: Current Infrastructure

AWS provided network segments

## Part 1: Prerequisites

```plaintext
sudo apt update && sudo apt upgrade -y && sudo apt install ufw wireguard -y #Install the wireguard and firewall packages
sudo ufw allow ssh && sudo ufw allow 51820/udp && sudo ufw allow 51822/udp && sudo ufw enable #Enable and allow Wireguard ports
sudo sysctl -w net.ipv4.ip_forward=1 && sudo sysctl -p /etc/sysctl.conf #Allows traffic forwarding
sudo su #Change to root user
cd /etc/wireguard/ && umask 077 && wg genkey | tee privatekey | wg pubkey > publickey #Generate private and public keys
cat privatekey && cat publickey #Note the private and public key
nano /etc/wireguard/wg2.conf
```

### Notes

1. The private key should not be shared, and is only used in the server config of the wg interface
2. The server public key is used on the client side to authenticate the client to the server associated to the port number.
3. Each client must have their own wg config file, and thus their own Listen Port. Refer to the Cheat Sheet for more info.
4. Decide on a network segment for the new profile being created. Subnet calculator can be found [here.](https://www.calculator.net/ip-subnet-calculator.html)

### Cheat sheet

| Server IP | Interface | Entity using | Port Number | IP Subnet | Public Key |
| --- | --- | --- | --- | --- | --- |
| 18.139.67.154 | wg0 | WBHS Group Servers | 51820 | 172.31.33.1/25 | N8JhuYZ6vSU2qHU+B0w9l8oW9rKQDKIsmjBV05aavSI= |
| 18.139.67.154 | wg1 | WBHS Group Employees | 51821 | 172.31.33.1/25 | N8JhuYZ6vSU2qHU+B0w9l8oW9rKQDKIsmjBV05aavSI= |
| 18.139.67.154 | wg2 | Koruna Assist | 51822 | 172.31.35.1/24 | N8JhuYZ6vSU2qHU+B0w9l8oW9rKQDKIsmjBV05aavSI= |
| 18.139.67.154 | wg3 | Kaesim Cybersecurity | 51823 | 172.31.36.1/24 | N8JhuYZ6vSU2qHU+B0w9l8oW9rKQDKIsmjBV05aavSI= |
| 13.239.127.37 | wg2 | Koruna Assist | 51822 | 172.31.24.1/24 | saHlWMKUAmb1/Ovx+p68mWinSevsA59QWg7zPb6kHE4= |

## Part 2: VPN Profiles - Config Files

### Singapore

#### wg0: WBHS Group Servers

```plaintext
root@ip-172-31-39-3:/home/ubuntu# cat /etc/wireguard/wg0.conf
## WBHS Group Servers ##
[Interface]
PrivateKey = aBjBoLGIuYXqiS7ifTbQ8PNe6pzVflYLK095ugL2OGA=
Address = 172.31.33.1/25
PostUp = ufw route allow in on wg0 out on ens5
PostUp = iptables -t nat -I POSTROUTING -o ens5 -j MASQUERADE
PreDown = ufw route delete allow in on wg0 out on ens5
PreDown = iptables -t nat -D POSTROUTING -o ens5 -j MASQUERADE
ListenPort = 51820

## William Asus ##
[Peer]
PublicKey = Z2eBbA4R/dNh0G+kyGVYO8VkprL5sa+Tl9MQTae4BC0=
AllowedIPs = 172.31.33.5/32
```

#### wg1: WBHS Group Employees

```plaintext
root@ip-172-31-39-3:/home/ubuntu# cat /etc/wireguard/wg1.conf
################
## WBHS Group ##
################
[Interface]
PrivateKey = aBjBoLGIuYXqiS7ifTbQ8PNe6pzVflYLK095ugL2OGA=
Address = 172.31.33.1/25
PostUp = ufw route allow in on wg0 out on ens5
PostUp = iptables -t nat -I POSTROUTING -o ens5 -j MASQUERADE
PreDown = ufw route delete allow in on wg0 out on ens5
PreDown = iptables -t nat -D POSTROUTING -o ens5 -j MASQUERADE
ListenPort = 51821

[Peer]
PublicKey = QI/nG/PNyCmKNKGlcd4vxkrzJlGQ9OnwSKgwMblGqBA=
AllowedIPs = 172.31.33.2/32
```

#### wg2: Koruna Assist

```plaintext
###################
## Koruna Assist ##
###################
[Interface]
PrivateKey = aBjBoLGIuYXqiS7ifTbQ8PNe6pzVflYLK095ugL2OGA=
Address = 172.31.35.1/24
PostUp = ufw route allow in on wg2 out on ens5
PostUp = iptables -t nat -I POSTROUTING -o ens5 -j MASQUERADE
PreDown = ufw route delete allow in on wg2 out on ens5
PreDown = iptables -t nat -D POSTROUTING -o ens5 -j MASQUERADE
ListenPort = 51822

[Peer]
PublicKey = +O4J5vJB4abyRHlAJFfWZ2ckB4SimcuVTJZ8LaKUTg8=
AllowedIPs = 172.31.35.11/32
```

#### wg3: Kaesim Cybersecurity

```plaintext
###########################
## Kaesim Cyber Security ##
###########################
[Interface]
PrivateKey = aBjBoLGIuYXqiS7ifTbQ8PNe6pzVflYLK095ugL2OGA=
Address = 172.31.36.1/24
PostUp = ufw route allow in on wg3 out on ens5
PostUp = iptables -t nat -I POSTROUTING -o ens5 -j MASQUERADE
PreDown = ufw route delete allow in on wg3 out on ens5
PreDown = iptables -t nat -D POSTROUTING -o ens5 -j MASQUERADE
ListenPort = 51823


## Gabi ##
[Peer]
PublicKey = YbL29Qo35FUduOoUUGHsKWxpwrG3m6LGP7BDRXS7QGw=
AllowedIPs = 172.31.36.11/32
```

### Australia

#### wg2: Koruna Assist

```plaintext
root@ip-172-31-22-132:/home/ubuntu# cat /etc/wireguard/wg2.conf 
###################
## Koruna Assist ##
###################
[Interface]
PrivateKey = wEThIL/bIb7k/skZJu2ltFeyjaQbRUv8p8sDrk9OGX0=
Address = 172.31.24.1/24
PostUp = ufw route allow in on wg2 out on ens5
PostUp = iptables -t nat -I POSTROUTING -o ens5 -j MASQUERADE
PreDown = ufw route delete allow in on wg2 out on ens5
PreDown = iptables -t nat -D POSTROUTING -o ens5 -j MASQUERADE
ListenPort = 51822


## Andreana Del Milana ##
[Peer]
PublicKey = usS3M5SHMrd2GgkltFk3WWJ8McR5yBa8pJcQcnUOUAA=
AllowedIPs = 172.31.24.11/32
```

### Notes

Comment every new wg config file to indicate the purpose. Also, comment every profile to indicate the user 

# Client Installation

## Windows Clients

[Windows Installer](https://download.wireguard.com/windows-client/wireguard-installer.exe)

1. Run the installation, making sure to run the as a service.
2. Click Create new empty tunnel

Configuring VPN Tunnel

### Base client config

```plaintext
Address = xxx.xxx.xxx.xxx/xx
DNS = 1.1.1.1

[Peer]
PublicKey = //**SERVER-PUBLIC-KEY**//
AllowedIPs = 0.0.0.0/0
Endpoint = xxx.xxx.xxx.xxx:518xx 
```

- Address corresponds to Client subnet
- Endpoint refers to the Server the Client will connect to. The port will correspond to the Client VPN profile

## Linux Clients

Linux clients should be done via config file.

## Server Side Client Addition