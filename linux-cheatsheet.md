# When computer frozen (Ubuntu 20.04)
	
	1. press <Alt> + <Print Screen> keys
	
	2. release  <Print Screen>

	3. type r-e-i-s-u-b

# Kill all processes of a user

	$ sudo killall --user <user-name>

# Kill all processes of an application

	$ sudo killall <application-name>

# Look up for location of a command

	$ which <cmd>

# Display one-line manual page descriptions 

	$ whatis <cmd>

# Run command as sudo

	$ sudo bash -c '<actual command>'

	# Note that if we don't use -c option then command such as sudo echo > ...somefile will not execute properly.


# List computer hardware information

	$ lshw

# List operating system information

	$ uname -a

# Add executable to environment path.

	$ Either editing ~/.bashrc or /etc/profile works but /etc/profile needs reboot.
	$ sudo vim ~/.bashrc

	# Add the following:
	
		export PATH=$PATH:<path-to-executable-directionary>

# Turn a computer into ssh server

	1. Install ssh

		$ sudo apt install ssh

	2. Open the firewall if on Ubuntu. Allow SSH if on Raspbian OS.

		$ sudo ufw allow ssh
	
		$ sudo ufw status verbose

	3. Start ssh daemon

		$ sudo systemctl start sshd

		 Check status

		$ sudo systemctl status sshd

		OR

		$ ps aux | grep <ps-name>

  If on the same network, try now with $ ssh <usr-name>@<ip-address> should work. If on different networj (different wifi router), proceed.


	4. Login to router control panel and add port forwarding port. For example, 777.

	5. Change login port Edit the /etc/ssh/sshd_config file.

			Port <port-number>

			Example: 420

	6. On the local client machine, generate a ssh key by:

			$ ssh-keygen 

	7. Install the public key to the server by:

			$ ssh-copy-id -i ~/.ssh/id_rsa.pub -p <port-number> <user-name>@<ip-address>

	8. In /etc/ssh/sshd_config, turn off password login.

				PasswordAuthentication no

	6. Restart sshd after every change to sshd_config

		$ sudo systemctl restart sshd

# ssh without password
	# Install sshpass 

	$ sudo apt install sshpass

	# when ssh/scp, use 'sshpass':

	$ sshpass -p '<password>' scp -o StrictHostKeyChecking=no <file-to-be-copied> <user-name>@<ip-addr/hostname>:<file-directory>
 

# Change hostname (Computer name)

	$ vim /etc/hostname

	$ sudo systemctl reboot

# Find out Linux kernel version

	$ cat /proc/version

# How to login to ssh server from private network?
	
	1. Find the name of user 

		$ who

	2. Find the private ip address

		$ ip addr

	3. Login

		$ ssh <who>@<private-ip-addr> -p <port>

# How to login to ssh server from public network?

	1. Find the the public address on google.

	2. Login
		
		$ ssh <user>@<public-ip-addr> -p <port>

# Transfer files with scp

	$ scp -P <port> <file> <username>@<ssh-host-machine>:<remote-path-to-stored-files>

	# multuple files
	$ scp -P <port> <file-A> <file-B> ... <file-Z> <username>@<ssh-host-machine>:<remote-path-to-store-files>

	# To find username 
	$ whoami

	# To find ssh_host_machine
	$ hostname

# Look up DNS domain name and get ip address.

	(!)DNS: Domain Naming System

	$ nslookup <domain-name>

	For example:

	nslookup www.google.com

# Print environment variables:

	$ printenv

# Find command executable location

	$ which <command>

# Create customized command for terminal

	1. Create a file "script.rc"
	2. Edit/Add new alias lines to this file 

			alias <command>="<command sequence 1;command sequence 2>"
			alias <command>="<command sequence 1;>"

	3. Add path of script.rc to .bashrc file in home directory

			Example:
			source /home/Scripts/script.rc

	4. Everytime the terminal opens up .bashrc file will be automatically loaded and thus scripts.rc alias will be created.

# kill a dead program

	$ ps aux | grep <program_name_keyword>

	# find the pid of the program

	$ kill <pid>

	# kill command can send many different type of signalsm not only kill

	$ kill -l 

# Get the last background running job's pid

	$ $!

# List computer operating system distribution

	$ cat /etc/os-release

# List Internet ports

	$ cat /etc/services


# List all the processes with their resource usage
	$ ps aux 

# Search for certain processes with keyword match from the list of all processes
	$ ps aux | grep <processes_keyword>

# List all processes in form of a tree

	$ pstree
# Print all environment variables
	$ printenv

# Scroll up/down in the terminal

	Shift + PgUp
	Shift + PgDn

# Run program in the background while surpressing output

	$ ./program &>/dev/null &

	Whatever written to /dev/null will be discarded, forgotten into the void in linux. 

# Embed one command in another

	Example:

	$ cp $(find . -name "A") ./target_folder/ 

# Dump object(executable) into readable file

	objdump -d <object> > <target_file>

# Create multiple files with similar names but same extension

	$ touch {<nameA, nameB, nameC>}.<same_extension>
	
# Find files with certain name and copy
	
	$ find . -name "*.pdf" -exec cp {} ./dest_folder \

# Find folders with certain name and remove

	$ rm -rf $(find . -type d -name ".git") 

# Find file with wildcard pattern matching
	
	$ find . -name "[1-9]_*"
	
	$ find . -name "*[A-Z][1-9]_*"

# Fina name in directory with maximal depth

	$ find . -name "<name>" -maxdepth <maxdepth>

# Find keyword in a single file

	$ grep '<keyword>' <path-to-file>

# Find keyword in a list of files 

	$ grep -rnw <path> -e <pattern>
	
		(!) there's no need for wildcard-matching symbol "*" before/after the <pattern>
	
		-r : recursive

		-n : line number

		-w : match the whole word


# List all files except for names that included certain keywords
	
	$ ls - I "name"

# List file size in MB
	
	$ ls -al --block-size=M

# Check directory size 

	$ du -sh <dir/file>

	$ du --summarize --human-readable <dir/file>
 
# List only directories 

	$ ls -d *.

	or

	$ ls -l | grep `^d'

# Copy files to a new folder created
	
	$ cp $(ls -I "folder_name") ./folder_name

# Sometimes large files > 100M are added
	
	# list large files
	
	$ find . -size +100M
	
	# remove them from repo cache
	
	$ git rm --cached <large file>

# Store script output to a file
	
	$ ./<script> | tee store.log

# Compress a folder to tar.gz
	
	$ tar -zcvf <folder-name>.tar.gz <folder-name>/ 

	(!) ".tar.gz" is the same as ".tgz"

	$ tar --create --file <name>.targ --verbose <source_folder_name>/

# Encrypt a file with gpg 
	
	Without using public-key cryptography (only a symmetric cipher)
	
	$ gpg --output <file>.gpg --symmetric <file>

# Decrypt with gpg

	$ gpg --output <file> --decrypt <file>.gpg 

# Split compressed files for each having a limited size
	
	$ split -b 100M <target>.tar.gz <target_splited> --verbose
	
	$ split --bytes=100M <target>.tar.gz <target_splited> --verbose
 

	For '<target_split>', the suggested name is e.g. "Installer_Splited_"
	
	Then the files created from the split will be automatically named:
	
	"Installer_Splited_aa", "Installer_Splited_ab", etc.  

# Remove all files in a folder except one/few
	
	$ rm !("file1")

	$ rm !("file1" | "file2") 

	$ rm -rf !("folder1")

# Remove a directory.

	$ rmdir <directory>

# Open a directory in GUI (Ubuntu)

	$ nautilus <dir>

# List all available UART serial ports

	$ ls /dev/tty*

# Find serial devices
	$ dmesg | grep tty

	# Expect something like:

		[20489.828127] usb 1-3.3.3: ch341-uart converter now attached to ttyUSB0

		or

		[20649.076411] ch341-uart ttyUSB0: ch341-uart converter now disconnected from ttyUSB0

# Install Debian Packages (.deb)

	$ dpkg --install <.deb>

	$ dpkg -i <.deb>

# Quit Lock Mode

	$ <Ctrl> + q

# Linux Root Folders

	"/" : the root

	"/bin" : "binary." Programs that are essential for the system to boot and run. 

	"/lib" : "library." contains libraries required by programs from the "/bin" folder

	"/boot" : It contains the linux kernel, initial RAM disk image, and the bootloader. 

	"/dev" : "device." It conatns files for all devices the Linux is able to recognize. 

		All the mouses, keyboards, and serial ports are here.
					
		> "tty" basically means terminal 

		> "sda" basically means harddrive

	"/etc" : "(E)dit (T)ext (C)onfigurations" Human readable text files for system-wide configurations. 

	"/home" : A base directory that contains all the regular users' files.

	"/media" : Used for automatic mounting of removable media such as USB drives, external hard disks, etc. 

	"/mnt" : "mount." Used for manually mounting of removable medias as USB drives, external hard disks, etc.

	"/opt" : "optionals." This is not essential to the OS. It is used to install third-party/user software and programs. 

	"/proc" : "processes." Virtual directory -- contains current systems information and processes in form of files and folders.
				
					 	It also contains a hierarchy of special files which represent the current state of the kernel.

						This allows applications and users to peer into the kernel's view of the system. 

						$ cat /proc/meminfo

						$ cat /proc/cpuinfo

						$ cat /proc/fs


# Some useful directories on Linux

	# Exported hardware devices by the kernel at runtime. You can control gpio and other peripherals by echo > <file> ... 
	$ cd /sys/class 

	For example if we want to generate a PWM output on Raspberry Pi 4B
	Edit /boot/config.txt
	On last line, add

	-> dtoverlay=pwm
	This enables the PWM in device tree

	$ sudo reboot

	$ echo 0 > /sys/class/pwm/pwmchip0/export # enable PWM0 on GPIO18

	$ echo 20000000 > sys/class/pwm/pwmchip0/pwm0/period # ns -> 50Hz

	$ echo 2000000 > sys/class/pwm/pwmchip0/pwm0/period # Duty cycle

	$ echo 1 > /sys/class/pwm/pwmchip0/pwm0/enable # Enable the PWM

	Plug in an osciloscope onto GPIO18 and we should observe 50Hz PWM.

<<<<<<< HEAD
  Another example is to turn on LED with sysfs
  
  $ echo 18 /sys/class/gpio/export # configure gpio 18

  $ echo out > /sys/class/gpio/gpio18/direction

  $ echo 1 > /sys/class/gpio/gpio18/value

   
=======
	# List the loaded device-tree nodes
	$ ls /proc/device-tree

	# List the kernel platform drivers	
	$ ls /sys/bus/platform/drivers

	# The directory where you can access the touchscreen input
	$ cd /dev/input/by-id
	$ sudo hexdump usb-ELAN_Touchscreen-event-if00


>>>>>>> bbbbfaa78e35c93048a058884aed2e661b024fbc

	 
# Run command at OS startup 

	$ sudo crontab -e

# Look for storage if not mounted. Sometimes if you just formated a disk, then you need to use fdisk.

	$ fdisk -l

# Look for a USB bulk device (storage device) if already mounted.

	$ lsblk

	# Look for names such as sda, sdb, sdc, etc. There might be several partitions on a same disk. For example, sda could be an entire physical hard drive, while sda1, sda2, sda3 are the partitions on it

# Format a bulk device. 

	# Format to ext4 (file system type for linux systems)

	$ sudo mkfs -t ext4 /dev/<bulk-device-name>

	# Format to FAT32 (Compatible with all MAC, Windows, or Linux)

	$ sudo mkfs -t vfat /dev/<bulk-device-name>

	# Format to NTFS (Read-Write on Windows only)

	$ sudo mkfs -t ntfs /dev/<bulk-device-name>


# Check free space / disk usage 

	$ df

# Mount a USB

	$ mkdir /media/<mount-point>

	$ mount /dev/<usb-device> /media/<mount-point>

# Unmount USB mount point

	$ umount /media/<mount_point>

	$ rm /media/<mount_point>

# Format a SD card 
	
	# Find the device 



# Create multiple files with same extension
	
	$ touch {<file_A>,<file_B>}.<extension>

# List network interfaces

	$ ifconfig

# Close certain network interface

	$ sudo ifconfig <interface> down

# Activate certain network interface

	$ sudo ifconfig <interface> up

# *ip* was designed to replace ifconfig command.
# Show ip address
	$ ip addr show 

# Display the routing table 
	$ ip route show

	(!) First line *default via* 172.31.16.1... This address is the address of the router.


# Check available wireless interfaces
	$ ip link

# Close certain network interface
	$ ip link set <interface> up

# Turn on certain network interface
	$ ip link set <interface> down

# Check if certain service is running

	$ sudo service <service_name> status

# Start service
	
	$ sudo service start <service_name>

# Stop service
	
	$ sudo service stop <service_name>

# Restart service

	$ sudo service restart <service_name>

# Search for historical command (reverse-i-search)

	$ Ctrl + R -> search upward

	$ Ctrl + Shift + R -> search downward

# Connect to wifi through command line

	# Scan for WIFI networks in range.
	$ sudo iwlist <interface> scan

	$ iwconfig <interface> essid <wifi_name> key <wifi_password>

	# Obtain the IP address through dhcp
	$ dhclient <interface>

# Check disk usage (du)
	
	(#) Total disk usage of current directory.
	$ du -sh

	$ du --summarize --human-readable

	(#) Disk usage for each files in the current directory

	$ du -sh *

# Show the status of module in the kernel.

	$ lsmod

# Delete a kernel module

	$ rmmod <module-name>

# Make block or character special files (in /dev/)
	
	# mknod

# Locate the location of a kernel module (so we can make a backup.)
	
	$ locate <module-name>

# Convert docx to pdf

	$ unoconv <file>

# Change system language to English

	$ sudo update-locale LANG=en_US.UTF-8

# Change font/font-size for TTY

	$ dpkg-reconfigure console-setup

# Get keycode mapping

	$ xmodmap -pk

# Convert PNG to JPG 

	$ mogrify -format JPG *.PNG

# Rotate video by 90 deg counterclockwise. 
ffmpeg -i <input-video> -vf "transpose=2" <output-video.mp4>

# Convert .mp4 to .mp3
ffmpeg -i <input-video.mp4> <output-audio.mp3>

# Cut video 
ffmpeg -i <input-video> -ss 00:00:27 -t 00:13:10 -c copy <output-video.mp4>

# Merge audio track with video
ffmpeg -i <input-video.mp4> -i <input-audio.mp3> -c copy -map 0:v:0 -map 1:a:0 <output.mp4>

# Enable authority level of certain device. 

	$ sudo chmod a+rw ./<executable>

	# a: all users
	# rw: read-write


