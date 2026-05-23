# overlayfs_root
a hook to load a linux system with a overlay root

heavily inspired by https://github.com/nils-werner/raspi-overlayroot

move the mount-root-overlayfs_hook to /etc/initcpio/hook and mount-root-overlayfs_install to /etc/initcpio/install
add mount-root-overlayfs to the HOOKS in /etc/mkinitcpio.conf

THIS HOOK SHOULD NOT WORK WITH SYSTEMD-BASED INITIAL RAM FILE SYSTEM

pass to the kernel the lowerdir as "root" anche the upperdir as "upperdir"

to have a ephemereal upper dir on tmpfs pass "tmpfs" to the "upperdir" argument

TODO:
→ support boot with a systemd-based initial ram file system
→ write a decentier README
???