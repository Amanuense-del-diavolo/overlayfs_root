# overlayfs_root

a hook to load a linux system with a overlay root

heavily inspired by https://github.com/nils-werner/raspi-overlayroot

## INSTALL

 - move `mount-root-overlayfs_hook` to `/etc/initcpio/hook/mount-root-overlayfs`
 - move `mount-root-overlayfs_install` to `/etc/initcpio/install/mount-root-overlayfs`
 - add `mount-root-overlayfs` to the HOOKS array in `/etc/mkinitcpio.conf`
 - add `overlay` to the MODULES array in `/etc/mkinitcpio.conf`
 - re-create the initramfs with `mkinitcpio -P`

**THIS HOOK SHOULD NOT WORK WITH SYSTEMD-BASED INITIAL RAM FILE SYSTEM**
to use Busybox instead of Systemd in the initramfs at least `systemd` should be replaced with `udev`
other changes may be required (depending on your specific configuration) for more info check the [arch wiki](https://wiki.archlinux.org/title/Mkinitcpio#Post_hooks)

**DON'T PUT /BOOT IN THE LOWERDIR, SINCE ALL THE CUSTOMIZATIONS WOULD BE WRITTEN TO THE UPPERDIR, PUT IT IN THE UPPERDIR OR (EVEN BETTER) ON A SEPARATE PARTITION**

## KERNEL PARAMETERS

to configure the kernel pass these values to the kernel line in the bootloader
 - pass the `lowerdir` as `root=XXXX`
 - pass the  `upperdir` as `upperdir=/dev/XXX`, for an ephemeral system pass `tmpfs` as the `upperdir` argument

**GRUB DOES NOT SUPPORT OVERLAYFS AS A ROOT FILESYSTEM**
it's anoyng since grub-mkconfig will not complete, I ran it while in a chroot inside the `lowerdir`, the `root` value will correct, but `lowerdir` would still ahve to be configured by hand

## TODO:

 → support boot with a systemd-based initial ram file system
 → write a decentier README
 → ???
