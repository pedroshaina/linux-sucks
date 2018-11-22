## Step by step instalation

pacman -Syu

pacman -S reflector rsync curl git

cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.bkp

reflector --verbose --country "Brazil" -l 5 --sort rate --save /etc/pacman.d/mirrorlist



```
parted /dev/sda
mklabel msdos
mkpart primary ext4 1MiB 512MiB
mkpart primary linux-swap 512MiB 2560MiB
mkpart primary ext4 2560MiB 100%
quit
```

```
fdisk /dev/sda
- n
- p
- (enter)
- (enter)
- +512M
- n
- p
- (enter)
- (enter)
- +2G
- n
- p
- (enter)
- (enter)
- (enter)
- w
```

```
mkfs.ext4 /dev/sda1
mkfs.ext4 /dev/sda3
mkswap /dev/sda2
swapon /dev/sda2

mount /dev/sda3 /mnt
mkdir /mnt/boot
mount /dev/sda1 /mnt/boot

pacstrap -i /mnt base base-devel

genfstab -U /mnt >> /mnt/etc/fstab

arch-chroot /mnt

sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen

locale-gen

echo LANG=en_US.UTF-8 > /etc/locale.conf

export LANG=en_US.UTF-8

echo "HOSTNAME" >> /etc/hostname

ln -sf /usr/share/zoneinfo/America/Sao_Paulo /etc/zoneinfo

sed -i -e 's/#\[multilib\]/\[multilib\]/' /etc/locale.gen /etc/pacman.conf
sed -i -e 's/#Include = \/etc\/pacman.d\/mirrorlist/Include = \/etc\/pacman.d\/mirrorlist/' /etc/pacman.conf

pacman -S grub
grub-install --recheck --target=i386-pc /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg

sed s/'# %wheel ALL=(ALL) ALL'/'%wheel ALL=(ALL) ALL'/ /etc/sudoers