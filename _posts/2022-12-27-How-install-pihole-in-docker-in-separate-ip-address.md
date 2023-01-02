---
author: Piragenth
tags:
- Docker
- How-To
Date: "2022-10-29"
categories:
- Docker
- How-to
- Linux
title: How to install pihole in docker in separate ip address
---
![](https://linuxtutorialforbeginners.com/assets/Pictures/update-pihole-running-in-a-docker-container.png)
# What is Pi-hole and why should you use it?

Pi-hole is an open source online ad blocker that works by intercepting Domain Name System (DNS) queries and blocking if it matches a list of specific ad serving domains. This can help reduce the number of unwanted ads you see when you're online and improve your online privacy by blocking tracking domains.

In addition to blocking ads, Pi-hole can also be used to block malicious domains, making it a useful tool for improving your network security.

## Assumptions

Before you start building Pi-hole on Docker using Macvlan, you need to make sure you have the following:

- Built for Mac and Docker
- Routers that support Dynamic Host Configuration Protocol (DHCP)

## Step 1: Create a new Macvlan network

To install Pi-hole on Docker using Macvlan, the first step is to create a new Macvlan network. This can be done by running the following command in a terminal window:

```bash
create docker network -d macvlan --subnet=192.168.1.0/24 --gateway=192.168.1.1 -o parent=eth0 macvlan_network
```

This command creates a new Macvlan network named "macvlan_network" using the Ethernet interface "eth0" as the primary interface. Also the subnet is 192.168.1.0/24 and the gateway is 192.168.1.1. You may need to adjust this value to match your network configuration.

## Step 2: Start the Pi-hole Docker container

Macvlan is installed and you can now run the Docker Pi-hole container on your Mac. To do this, run the following command:

```bash
docker run -d --name pihole --restart = always -p 53:53/tcp -p 53:53/udp -p 80:80 -v/etc/pihole/:/etc/pihole/-v/etc/ dnsmasq.d/:/etc/dnsmasq.d/ --network macvlan_network --ip 192.168.1.100 pihole/pihole
```


This command starts a new Docker container named "pihole" and linked to "macvlan_".

## Step 3: Configure your router's DHCP server

Once the Pi-hole container is running, you need to configure your router's DHCP server to act as a DNS server for your network. To do this, log into the router's web interface and open the DHCP settings. Add the IP address of the Pi-hole container (192.168.1.100 in our example) as the primary DNS server and any other DNS server you want to use as the secondary server.

## Step 4: Test the Pi-hole setup

With the Pi-hole container running and your router's DHCP server configured to use it, you can now use Pi-hole as your network's DNS server. To test it, open a few web pages on your Mac or other network-connected device. If the site is on the block list, you should see a message that Pi-hole has been blocked.

## Step 5: Configure Pi-hole settings

You can access the Pi-hole web interface at http://192.168.1.100/admin (replace 192.168.1.100 with the IP address of your Pi-hole container). Here you can change various settings such as block list used, DNS server used, white list and black list.

## Step 6: Install a system ad blocker

Pi-hole can block ads on all devices connected to your network, not just those with the Pi-hole client installed. To set this up, you need to configure your device to use Pi-hole as a DNS server. On a Mac, you can do this by going to System Preferences > Network > Advanced > DNS and adding the IP address of the Pi-hole container as a DNS server. On other devices, you should refer to the device's documentation to learn how to change the DNS settings.

## Step 7: Monitor Pi-hole operation

Pi-hole's web interface provides a number of useful statistics, including the number of ads blocked, the most requested domains, and the largest subscribers on the network. You can use this information to monitor your Pi-hole's performance and make necessary adjustments to your settings.

## Step 8: Consider using Pi-hole's FTLDNS service

Pi-hole FTLDNS is a more efficient and customizable version of Pi-hole available as a standalone Docker container. If you want to take advantage of its advanced features, you can run both the FTLDNS container and the Pi-hole container using the same Macvlan network.

## Conclusion

Building a Pi-hole on Docker with macvlan is a great way to install a network ad blocker on your Mac. If you follow the steps in this guide, you'll never have to leave your Pi-hole running again. With powerful blocking features and customizable settings, Pi-hole is a great tool to improve your online privacy and security.