---
title: "How to install Arch Linux with KDE plasma"
date: 2022-11-22T08:11:49+05:30
draft: false
tag:
  - Docker
  - How-To
---
![](https://linuxtutorialforbeginners.com/assets/Pictures/install-kde-arch-linux.webp)

# Installing Arch Linux with KDE Plasma and SDDM

Installing Arch Linux can be a daunting task for those new to the world of Linux, but with a little bit of guidance and patience, it can be a rewarding experience. In this tutorial, we will guide you through the process of installing Arch Linux with KDE Plasma desktop environment and Simple Desktop Display Manager (SDDM) on your system.

Before we begin, it's important to note that this tutorial assumes that you have some basic knowledge of Linux and are comfortable with using the command line. If you are new to Linux, it might be helpful to familiarize yourself with some basic concepts and commands before proceeding.

Here are the steps you will need to follow to install Arch Linux with KDE Plasma and SDDM:

## Pre-installation tasks
Before you begin the installation process, there are a few things you should do to prepare your system:

Download the latest Arch Linux ISO from the official website (https://www.archlinux.org/download/) and create a bootable USB or DVD.

Backup your important data. Installing a new operating system can be risky, so it's always a good idea to backup your data before proceeding.

Check your system's hardware requirements. Arch Linux has relatively low hardware requirements, but it's always a good idea to check that your system meets the minimum requirements for KDE Plasma.

Check your internet connection. You will need an internet connection to install Arch Linux and its packages.

## Boot into the Arch Linux installation media

Once you have prepared your system and created the bootable installation media, it's time to boot into the Arch Linux installation environment. To do this, insert the installation media into your system and restart your computer.

On most systems, you will need to enter the BIOS or UEFI settings and change the boot order to boot from the installation media first. Consult your motherboard's documentation or do a quick online search to find out how to enter the BIOS or UEFI settings on your particular system.

Once you have changed the boot order, save your changes and exit the BIOS or UEFI settings. Your system should now boot into the Arch Linux installation environment.

## Connect to the internet
Once you have booted into the Arch Linux installation environment, you will need to connect to the internet. If you are using a wired connection, you should be able to connect automatically. If you are using a wireless connection, you will need to use the wifi-menu command to connect to your wireless network.

## Update the system clock
Before you begin the installation process, it's a good idea to update the system clock to the current date and time. To do this, use the timedatectl command as follows:

```bash
timedatectl set-ntp true
```
## Partition the disk
Next, you will need to partition your disk to create space for Arch Linux. There are many different ways to partition a disk, and the method you choose will depend on your particular needs and preferences.

Here is one example of how you could partition your disk:

Create a small partition (around 500MB) for the boot partition. This partition will be used to store the bootloader and the Linux kernel.

Create a larger partition (around 20GB) for the root partition. This partition will be used to store the core system files and packages.

Create a swap partition (around the same size as your system's RAM) for swap space. Swap space is used as virtual memory when your system runs out of physical RAM.

Create a home partition (the rest of the available space) for user home directories. This is where all of your user data will be stored.

Once you have decided how you want to partition your disk, you can use the cfdisk command to set it up. Consult the Arch Wiki for detailed instructions on how to use cfdisk to partition your disk.

## Format the partitions
Once you have partitioned your disk, you will need to format the partitions with a filesystem. For the boot partition, you will need to use a supported boot filesystem, such as FAT32 or ext4. For the root, swap, and home partitions, you can use either ext4 or XFS.

You can use the mkfs command to format the partitions with the appropriate filesystems. For example, to format the root partition with ext4, you would use the following command:

```bash
mkfs.ext4 /dev/sda2
```
## Mount the partitions
Once you have formatted the partitions, you will need to mount them to their respective mount points. For example, the root partition would be mounted to /, the home partition to /home, and so on.

You can use the mount command to mount the partitions. For example, to mount the root partition to /, you would use the following command:

```bash
mount /dev/sda2 /
```
## Install the base system
Now that all of the partitions have been prepared and mounted, it's time to install the base system. This can be done with the pacstrap command.

This command will download and install all of the necessary base packages for Arch Linux. Once the installation is complete, you will need to generate the fstab file which is used to specify which partitions should be mounted at boot.

You can generate the fstab file with the genfstab command.

```bash
genfstab -U / > /etc/fstab
```
## Chroot into the new system
Now that the base system has been installed and the fstab file has been generated, you will need to chroot into the new system. To do this, use the arch-chroot command.

```bash
arch-chroot /mnt
```
## Configure the system
Once you have chrooted into the new system, you will need to configure it before it can be used. This will include setting the timezone, creating a user account, setting the hostname, and more.

To set the timezone, use the ln command to create a symbolic link from the /etc/localtime to the appropriate timezone file located in /usr/share/zoneinfo.

To create a user account, use the useradd command, followed by the passwd command to set the account’s password.

To set the hostname, use the hostnamectl command.

## Install the bootloader
Once the system has been configured, you will need to install the bootloader. The bootloader is responsible for loading the Linux kernel at boot.

On most systems, you will need to use a program such as GRUB to install the bootloader. To install GRUB, use the grub-install command.

## Install KDE Plasma and SDDM
Once the bootloader has been installed, it's time to install KDE Plasma and SDDM. To do this, first use the pacman command to install the plasma-desktop and sddm packages.

```bash
pacman -S plasma-desktop sddm
```
Once the packages have been installed, use the systemctl command to enable the sddm service.

```bash
systemctl enable sddm.service
```

Finally, reboot your system and you should be greeted with the KDE Plasma desktop environment and the SDDM login screen.

Congratulations! You have successfully installed Arch Linux with KDE Plasma and SDDM.

alternativly you can also use automated script to install arch: https://github.com/christitustech/archtitus
