# dotfiles

Dustin's dotfiles.

Installed packages: 
```
i3
i3-blocks
zsh
oh-my-zsh
qutebrowser
rxvt-unicode
```

## ArchLinux installation

https://wiki.archlinux.org/index.php/installation_guide

### Disk
Partitioning:
```
# fdisk /dev/sda
---
Command: o

Command: n
Partition number: 1
First sector: 2048
Last sector: +512M

Command: n
Partition number: 2
First sector: default
Last sector: +4096M

Command: t
Partition number: 2
Hex code: 82

Command: n
Partition number: 3
First sector: default
Last sector: default

Command: w
```

Formatting:
```
# mkfs.ext2 /dev/sda1
# mkfs.ext4 /dev/sda3
# mkswp /dev/sda2
```

Mount File Partitions:
```
# mount /dev/sda3 /mnt
# swapon /dev/sda2
```

### Installation
Edit mirrors list:

`# vim /etc/pacman.d/mirrorlist`

Install `base` packages:

`# pacstrap /mnt base base-devel`

### Configure the system
Generate fstab file:

`# genfstab -U /mnt >> /mnt/etc/fstab`

chroot:

`# arch-chroot /mnt`

Timezone/Localization/Network Configuration/Root password: defaults

### Bootloader
Install and configure GRUB:
```
# pacman -S grub
# grub-install /dev/sda
# grub-mkconfig -o /boot/grub/grub.cfg
```

### Reboot
Follow instructions.

## Post-Install
Packages:
```
wpa_supplicant
xorg-server
xorg-apps
xorg-xinit
vim
i3 (i3-gaps)
mlocate
xf86-video-vesa
ttf-dejavu
git
xf86-video-intel
dmenu
rxvt-unicode
libxft
xorg-xbacklight
alsa-utils
xorg-xev
pulseaudio
pulseaudio-alsa
feh
xorg-xset
zsh (oh-my-zsh)
openssh
```




