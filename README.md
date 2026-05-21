# overlayfs_root
a hook to load a linux system with a overlay root

move the mount-root-overlayfs_hook to /etc/initcpio/hook and mount-root-overlayfs_install to /etc/initcpio/install
add mount-root-overlayfs to the HOOKS in /etc/mkinitcpio.conf

THIS HOOK SHOULD NOT WORK WITH SYSTEMD-BASED INITIAL RAM FILE SYSTEM

pass to the kernel the lowerdir as "root" anche the upperdir as "upperdir"

it does not support tmpfs for the upperdir

TODO:
→ support boot with a systemd-based initial ram file system
→ support tmpfs for the upperdir for an ephemereal system
???