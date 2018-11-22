# Arch Linux workstation setup guide

### Setup basic Operating System
- Check internet connection or use wifi-menu to setup wireless connection
- Change (create) the root password of the LiveCD Arch Installation and ssh into it
- Update the packages
- Install reflector to get the fastest mirror
- Partition the disk with a 500M bootable boot partition and a root partition with the remaining free space
- Create the filesystem
- Mount the root partition to /mnt, create the folder /mnt/boot and mount boot partition to it
- Run pacstrap against /mnt to install the base packages
- Generate the fstab file
- Change root into the new system mounted on /mnt
- Set hostname
- Set timezone
- Generate locales
- Change root password
- Install bootloader
- Create initial RAM disk
- Install and enable NetworkManager
- Install and enable SSH
- Unmount and reboot

### If running a baremetal install you may want to:
- Install Bluetooth and load the module onto the kernel
- if on a laptop, install touchpad input drivers
- You may want to use UEFI
- You may want to encrypt root partition

### Setup display server and make it usable
- Enable multilib
- Install X11
- Install video drivers
- Install useful packages (check list)
- Create a user (with sudo rights) to daily usage
- Install audio packages
- Install a Desktop Environment and a Display Manager
- Enable the choosen DM and reboot

### What did I do wrong?
- Check the steps your are stuck on the [Installation Guide](https://wiki.archlinux.org/index.php/Installation_guide) 
- Did you generate fstab? Did you create the initial ramdisk?
- Check logs
- Start from the scratch
- Read the [Arch Wiki](https://wiki.archlinux.org) (It's awesome)

## Step by step instalation 

[Commands used](INSTALATION.md) 

[Tips on using Arch](TIPS.md)



