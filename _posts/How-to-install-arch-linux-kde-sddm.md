Congratulations on choosing to install Arch Linux! In this tutorial, we will guide you through the process of installing Arch Linux with the KDE desktop environment and the SDDM display manager.

Before we begin, it is important to note that Arch Linux is a rolling release distribution, which means that it is constantly updated and there are no "versions" of Arch Linux. This means that some of the steps in this tutorial may change over time as Arch Linux is updated. It is always a good idea to check the Arch Linux documentation for the most up-to-date information.

With that said, let's get started!

Step 1: Prepare the installation media

The first step in installing Arch Linux is to prepare the installation media. You will need a USB drive or CD/DVD with at least 512 MB of storage.

To create the installation media, you can either download the Arch Linux ISO from the official website and use a tool like Rufus (for Windows) or Etcher (for Mac and Linux) to create the bootable USB drive, or you can use the dd command to write the ISO to a USB drive or CD/DVD.

For example, to write the ISO to a USB drive using dd, open a terminal and enter the following command (replace /dev/sdX with the device name of your USB drive):

Copy code
sudo dd if=archlinux.iso of=/dev/sdX bs=4M status=progress oflag=sync
Step 2: Boot from the installation media

Next, insert the installation media into your computer and boot from it. The process for booting from the installation media will vary depending on your computer's BIOS/UEFI settings. Consult your computer's documentation or do an online search for instructions on how to boot from a USB drive or CD/DVD on your specific model of computer.

Step 3: Connect to the internet

Once you have booted from the installation media, you will be presented with a command prompt. The first thing you will need to do is connect to the internet so that you can download and install packages.

To connect to the internet using a wired Ethernet connection, enter the following command:

Copy code
dhcpcd
If you are using a wireless connection, you will need to first load the necessary kernel modules by entering the following command:

Copy code
modprobe -a iwldvm iwlwifi
Then, use the wifi-menu command to connect to a wireless network. Follow the prompts to select your wireless network and enter the password.

Step 4: Partition the disk

Before we can install Arch Linux, we need to partition the disk and create a filesystem on it. We will use the fdisk utility to partition the disk.

First, use the fdisk -l command to list all of the available disks on your system. Make note of the device name of the disk you want to install Arch Linux on (e.g. /dev/sda, /dev/sdb, etc.).

Next, enter the fdisk utility by typing fdisk /dev/sda (replace /dev/sda with the device name of your disk).

Inside the fdisk utility, you will need to create at least two partitions: a boot partition and a root partition. The boot partition should be around 200 MB and the root partition should take up the rest of the disk space.

To create a partition, type n and then press enter. You will then be prompted to select the type of partition you want to create (primary, extended, or logical). Select the type of partition you want to create and press enter. You will then be prompted to select the start and end sectors for the partition. You can accept the default values by pressing enter.

Once you have created the partitions, type w to write the changes to the disk.

Step 5: Format the partitions

Now that we have partitioned the disk, we need to format the partitions. To do this, we will use the mkfs utility.

First, use the lsblk command to list all of the partitions on the disk. Make note of the device names for the boot and root partitions (e.g. /dev/sda1 and /dev/sda2).

Next, format the boot partition as an ext2 filesystem by entering the following command (replace /dev/sda1 with the device name of your boot partition):

Copy code
mkfs.ext2 /dev/sda1
Finally, format the root partition as an ext4 filesystem by entering the following command (replace /dev/sda2 with the device name of your root partition):

Copy code
mkfs.ext4 /dev/sda2
Step 6: Mount the partitions

Now that we have formatted the partitions, we need to mount them. To do this, we will use the mount command.

First, create a mount point for the boot partition by entering the following command:

Copy code
mkdir /mnt/boot
Next, create a mount point for the root partition by entering the following command:

Copy code
mkdir /mnt/root
Finally, mount the partitions by entering the following commands (replace /dev/sda1 and /dev/sda2 with the device names of your partitions):

Copy code
mount /dev/sda1 /mnt/boot
mount /dev/sda2 /mnt/root
Step 7: Install the base system

Now that we have prepared the disk and mounted the partitions, we can install the base system. To do this, we will use the pacstrap command.

Enter the following command to install the base system (replace /mnt/root with the mount point of your root partition):

Copy code
pacstrap /mnt/root base
This will install the base system, which includes the Linux kernel and some basic utilities.

Step 8: Configure the system

Now that we have installed the base system, we need to configure it. To do this, we will use the arch-chroot command.

Enter the following command to enter the Arch Linux system:

Copy code
arch-chroot /mnt/root
Once you have entered the system, you will need to set the system time zone by entering the following command (replace America/New_York with the time zone for your location):

Copy code
ln -sf /usr/share/zoneinfo/America/New_York /etc/localtime
Next, generate the system locale by entering the following command:

Copy code
locale-gen
Finally, create a hostname for the system by entering the following command (replace archlinux with a hostname of your choice):

Copy code
echo archlinux > /etc/hostname
Step 9: Install the bootloader

Now that we have configured the system, we need to install the bootloader. We will use the GRUB bootloader.

First, install the GRUB package by entering the following command:

Copy code
pacman -S grub
Next, install the GRUB bootloader by entering the following command (replace /dev/sda with the device name of your disk):

Copy code
grub-install /dev/sda
Finally, generate the GRUB configuration file by entering the following command:

Copy code
grub-mkconfig -o /boot/grub/grub.cfg
Step 10: Install the desktop environment and display manager

Now that we have installed the bootloader, we can install the desktop environment and display manager. We will install the KDE desktop environment and the SDDM display manager.

First, install the KDE packages by entering the following command:

Copy code
pacman -S kde-applications
Next, install the SDDM display manager by entering the following command:

Copy code
pacman -S sddm
Finally, enable the SDDM service by entering the following command:

Copy code
systemctl enable sddm
Step 11: Reboot the system

Now that we have installed the desktop environment and display manager, we can reboot the system. To do this, enter the following command:

Copy code
exit
Then, unmount the partitions by entering the following commands (replace /mnt/boot and /mnt/root with the mount points of your partitions):

Copy code
umount /mnt/boot
umount /mnt/root
Finally, reboot the system by entering the following command:

Copy code
reboot

And that's it! Your Arch Linux system is now installed with the KDE desktop environment and the SDDM display manager. Enjoy your new system!
