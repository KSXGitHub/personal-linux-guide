# Error Message

```
Not syncing: No working init found. Try passing init= option to kernel. See Linux Documentatio/<...> fot guidance.
```

# Cause

Fucked up system symbolic links (such as `/usr/lib64` does not exist).

# Fix

**Step 1:** Boot an ArchLinux Live USB/DVD, Arch derivatives (such as Antergos, Manjaro) also work as long as they provide arch's tools

**Step 2:** Enter the following command

```sh
# Mount your hard drive which contains the operating system that you're trying to fix
# It was /dev/sda5 in my case
mount /dev/sda5 /mnt

# Change root to the operating system that you're trying to fix
arch-chroot /mnt

# Fix the fucked up filesystem
pacman -S filesystem

# Recreate boot loader
mkinitcpio -p linux
grub-mkconfig -o /boot/grub/grub.cfg

# Blah, blah, you know the rest
exit
umount -R /mnt
reboot
```

# Source

https://bbs.archlinux.org/viewtopic.php?pid=1494629#p1494629
