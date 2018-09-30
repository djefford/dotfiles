# dotfiles

Dustin's dotfiles.

Installed packages: 
```
i3
i3-blocks
zsh
oh-my-zsh
qutebrowser
```

## ArchLinux installation

https://wiki.archlinux.org/index.php/installation_guide

### Disk
Partitioning:
```
# fdisk -l /dev/sda

Command: g
Command: n
Partition number: 1
First sector: 2048
Last sector: 1499135

Command: t
Partition type: 4

Command: n
Partition number: 2
First sector: 1499136
Last sector: default

Command: w
```

Formatting:
```
# mkfs.ext2 /dev/sda1
# mkfs.ext4 /dev/sda2
```

Mount File Partitions:
```
# mount /dev/sda2 /mnt
# mkdir /mnt/boot
# mount /dev/sda1 /mnt/boot
```

### Installation
Edit mirrors list:

`# vim /etc/pacman.d/mirrorlist`

Install `base` packages:

`# pacstrap /mnt base`

### Configure the system
Generate fstab file:

`# genfstab -U /mnt >> /mnt/etc/fstab`

chroot:

`# arch-chroot /mnt`

Swap file creation:
```
# dd if=/dev/zero of=/swapfile bs=1M count=512
# chmod 600 /swapfile
# mkswap /swapfile
# swapon /swapfile
# vi /etc/fstab
---
/swapfile none swap defaults 0 0
```

Set time:

```
# ln -sf /usr/share/zoneinfo/America/Indianapolis /etc/localtime
# hwclock --systohc
```


