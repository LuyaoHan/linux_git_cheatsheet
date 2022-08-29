# Install QEMU

# Two things needed for linux to boot:
1. built linux kernel 
2. rootfs (use ramdisk)

# qemu-system-x86_64 -kernel arch/x86_64/boot/bzImage
Expect kernel panic

# Minimal:
# qemu-system-x86_64 -kernel arch/x86_64/boot/bzImage initrd ramdisk.img
