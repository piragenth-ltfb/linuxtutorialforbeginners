---
author: Piragenth
title: "How to install Arch Linux with KDE plasma"
date: 2022-11-22T08:11:49+05:30
suggestion: false
categories:
  - Docker
  - How-to
---
![](https://linuxtutorialforbeginners.com/assets/Pictures/install-kde-arch-linux.webp)

# Installing Arch Linux with KDE Plasma and SDDM

Installing Arch Linux can be a daunting task for those new to the Linux world, but with a little guidance and patience, it can be a rewarding experience. In this tutorial, we will walk you through the process of installing Arch Linux with the KDE Plasma desktop environment and Simple Desktop Display Manager (SDDM) on your system.

Before we begin, it's important to note that this tutorial assumes that you have some basic knowledge of Linux and that you're comfortable using the command line. If you are new to Linux, it may be helpful to familiarize yourself with some basic concepts and commands before proceeding.

Here are the steps you will need to follow to install Arch Linux with KDE Plasma and SDDM:

## Pre-installation tasks
Before you begin the installation process, there are a few things you should do to prepare your system:

Download the latest Arch Linux ISO from the official site (https://www.archlinux.org/download/) and create a bootable USB or DVD.

Back up important data. Installing a new operating system can be risky, so it's always a good idea to back up your data before proceeding.

Check the hardware requirements of your system. Arch Linux has relatively low hardware requirements, but it's always a good idea to check that your system meets the minimum requirements for KDE Plasma.

Check your internet connection. You will need an internet connection to install Arch Linux and its packages.

## Boot the Arch Linux installation media

Once you've prepared your system and created a bootable installation media, it's time to boot into the Arch Linux installation environment. To do this, insert the installation media into the system and restart the computer.

On most systems, you will need to enter the BIOS or UEFI settings and change the boot order to boot from the installation media first. To find out how to enter the BIOS or UEFI settings on your particular system, check your motherboard documentation or do a quick online search.

Once you change the boot order, save the changes and exit BIOS or UEFI setup. Your system should now boot into the Arch Linux installation environment.

## Connect to the Internet
Once you've booted into the Arch Linux installation environment, you'll need to connect to the Internet. If you are using a wired connection, you should be able to connect automatically. If you are using a wireless connection, you will need to connect to the wireless network using the wifi-menu command.

## Update the system clock
Before starting the installation process, it is a good idea to update the system clock to the current date and time. To do this, use the timedatectl command like this:

``` bash
timedatectl set-ntp true
```
## Partition the disk
Next, you'll need to partition the drive to make room for Arch Linux. There are many different ways to partition a disk, and the way you choose will depend on your specific needs and preferences.

Here is one example of how you can partition a disk:

Create a small partition (around 500 MB) for the boot partition. This partition will be used to store the bootloader and Linux kernel.

Create a larger partition (around 20 GB) for the root partition. This partition will be used to store core system files and packages.

Create a swap partition (about the same size as your system's RAM) for the swap space. Swap space is used as virtual memory when your system runs out of physical RAM.

Create a home partition (the rest of the available space) for users' home directories. All your user data will be stored here.

Once you've decided how you want to partition the disk, you can set it up using the cfdisk command. See the Arch Wiki for detailed instructions on how to use cfdisk to partition a disk.

## Format the partitions
Once you've partitioned the drive, you'll need to format the partitions using the file system. You will need to use a supported bootable file system such as FAT32 or ext4 for the boot partition. You can use ext4 or XFS for root, swap and home partitions.

You can format partitions with appropriate file systems using the mkfs command. For example, to format the root partition with ext4, you would use the following command:

``` bash
mkfs.ext4 /dev/sda2
```
## Mount the partitions
Once you've formatted the partitions, you'll need to mount them to their respective mount points. For example, the root partition will be mounted to /, the home partition to /home, and so on.

You can use the mount command to mount partitions. For example, to mount the root partition to /, use the following command:

``` bash
mount /dev/sda2 /
```
## Install the base system
Now that all the partitions are ready and connected, it's time to install the base system. This can be done using the pacstrap command.

This command will download and install all necessary core packages for Arch Linux. After the installation is complete, you will need to generate an fstab file that is used to determine which partitions to mount at boot time.

You can generate an fstab file using the genfstab command.

``` bash
genfstab -U /> /etc/fstab
```
## Chroot to the new system
Now that the base system is installed and the fstab file is generated, you will need to chroot into the new system. To do this, use the arch-chroot command.

``` bash
arch-chroot /mnt
```
## Configure the system
Once you've chrooted into your new system, you'll need to configure it before you can use it. This will include setting the time zone, creating a user account, setting the hostname, and more.

To set the time zone, use the ln command to create a symbolic link from /etc/localtime to the appropriate time zone file located in /usr/share/zoneinfo.

To create a user account, use the useradd command and then the passwd command to set the account password.

To set the hostname, use the hostnamectl command.

## Install bootloader
Once the system is configured, you will need to install the bootloader. The bootloader is responsible for loading the Linux kernel at boot time.

On most systems, you'll need to use a program like GRUB to install the bootloader. To install GRUB, use the grub-install command.

## Install KDE Plasma and SDDM
Once the bootloader is installed, it's time to install KDE Plasma and SDDM. To do this, first use the pacman command to install the plasma-desktop and sddm packages.

``` bash
pacman -S plasma-desktop sddm
```
Once the packages are installed, use the systemctl command to enable the sddm service.

``` bash
systemctl enable sddm.service
```

Finally reboot the system and you should be g