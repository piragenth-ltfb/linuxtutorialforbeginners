---
author: piragenth
categories:
- Docker
- how-to
date: "2022-10-29"
tags:
- Docker
- How-TO
- Linux
title: How to install pihole in docker in separate ip address
---
![](https://linuxtutorialforbeginners.com/assets/Pictures/update-pihole-running-in-a-docker-container.png)
# What is Pi-hole and why would you want to use it?

Pi-hole is an open-source network-wide ad blocker that works by intercepting DNS (Domain Name System) queries and blocking them if they match a list of known ad-serving domains. This can help to reduce the amount of unwanted ads that you see when browsing the web, and can also help to improve your online privacy by blocking tracking domains.

In addition to blocking ads, Pi-hole can also be used to block malicious domains, making it a useful tool for improving the security of your network.

## Prerequisites

Before you can start installing Pi-hole on Docker using Macvlan, you'll need to make sure that you have the following:

- A Mac with Docker installed
- A router that supports DHCP (Dynamic Host Configuration Protocol)

## Step 1: Create a new Macvlan network

The first step in installing Pi-hole on Docker using Macvlan is to create a new Macvlan network. This can be done by running the following command in a terminal window:

```bash
docker network create -d macvlan --subnet=192.168.1.0/24 --gateway=192.168.1.1 -o parent=eth0 macvlan_network
```

This command creates a new Macvlan network called "macvlan_network" using the Ethernet interface "eth0" as the parent interface. It also sets the subnet to 192.168.1.0/24 and the gateway to 192.168.1.1. You may need to adjust these values to match your network's configuration.

## Step 2: Run the Pi-hole Docker container

With the Macvlan network set up, you can now start a Pi-hole Docker container on your Mac. To do this, run the following command:

```bash
docker run -d --name pihole --restart=always -p 53:53/tcp -p 53:53/udp -p 80:80 -v /etc/pihole/:/etc/pihole/ -v /etc/dnsmasq.d/:/etc/dnsmasq.d/ --network macvlan_network --ip 192.168.1.100 pihole/pihole
```


This command starts a new Docker container with the name "pihole" and connects it to the "macvlan_

## Step 3: Configure your router's DHCP server

Now that the Pi-hole container is running, you'll need to configure your router's DHCP server to use it as the DNS server for your network. To do this, log into your router's web interface and navigate to the DHCP settings. Add the IP address of the Pi-hole container (192.168.1.100 in our example) as the primary DNS server, and any other DNS servers you want to use as the secondary servers.

## Step 4: Test your Pi-hole installation

With the Pi-hole container running and your router's DHCP server configured to use it, you should now be able to use Pi-hole as your network's DNS server. To test this, try visiting a few websites on your Mac or any other device connected to the network. You should see a message indicating that the website is blocked by Pi-hole if it is on the blocklist.

## Step 5: Configure Pi-hole's settings

You can access the Pi-hole web interface by visiting http://192.168.1.100/admin (replace 192.168.1.100 with the IP address of your Pi-hole container). From here, you can change various settings such as the blocklists used, the DNS servers used, and the whitelist and blacklist.

## Step 6: Set up the network-wide ad blocker

Pi-hole can block ads on all devices connected to your network, not just the ones that have the Pi-hole client installed. To set this up, you'll need to configure your devices to use Pi-hole as their DNS server. On your Mac, you can do this by going to System Preferences > Network > Advanced > DNS and adding the IP address of the Pi-hole container as a DNS server. On other devices, you'll need to consult the device's documentation to find out how to change the DNS settings.

## Step 7: Monitor Pi-hole's performance

The Pi-hole web interface provides a number of useful statistics, including the number of ads blocked, the top domains queried, and the top clients on the network. You can use this information to monitor the performance of Pi-hole and make any necessary adjustments to the settings.

## Step 8: Consider using the Pi-hole FTLDNS service

The Pi-hole FTLDNS service is a more efficient and customizable version of Pi-hole that is available as a separate Docker container. If you want to take advantage of its advanced features, you can run the FTLDNS container alongside the Pi-hole container by using the same Macvlan network.

## Conclusion

Installing Pi-hole on Docker using Macvlan is a great way to set up a network-wide ad blocker on your Mac. By following the steps outlined in this tutorial, you should be able to get Pi-hole up and running in no time. With its powerful blocking capabilities and customizable settings, Pi-hole is an excellent tool for improving your online privacy and security.
