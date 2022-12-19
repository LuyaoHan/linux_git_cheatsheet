# Install QEMU

	$ sudo apt-get install qemu-system

# Download raspbian kernel

	Latest qemu kernel: https://github.com/dhruvvyas90/qemu-rpi-kernel

# Start QEMU to emulate rapbian

	$ qemu-system-arm 
	  -kernel ~/Projects/raspbian_qemu/qemu-rpi-kernel/kernel-qemu-4.19.50-buster \
      -cpu arm1176 \
      -m 256 \ 
      -M versatilepb \
      -serial stdio \ 
      -append "root=/dev/sda2 rootfstype=ext4 rw" \
 	  -hda ~/Projects/raspbian_qemu/2022-09-22-raspios-buster-armhf.img \
      -dtb qemu-rpi-kernel/versatile-pb-buster-5.4.51.dtb

