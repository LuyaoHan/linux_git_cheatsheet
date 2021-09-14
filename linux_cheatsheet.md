# (!)When computer frozen (Ubuntu 20.04)
	
	1. press <Alt> + <Print Screen> keys
	2. release  <Print Screen>
	3. type r-s-i-s-u-b

# (!) Create customized command for terminal

	1. Create a file "script.rc"
	2. Edit/Add new alias lines to this file 
			alias <command>="<command sequence 1;command sequence 2>"
			alias <command>="<command sequence 1;>"
	3. Add path of script.rc to .bashrc file in home directory
			Example:
			source /home/Scripts/script/rc
	4. Everytime the terminal opens up .bashrc file will be automatically loaded and thus scripts.rc alias will be created.

# Ubuntu-specific Applications 
	PDF viewer: Okular (install through snapd, better version compared to source from apt)
	Web automation: google-chrome
	File browser: Nautilus
	Text editor: Vim-gtk3


# Scroll up/down in the terminal

	Shift + PgUp
	Shift + PgDn

# Run program in the background while surpressing output

	$ ./program &>/dev/null &

	Whatever written to /dev/null will be discarded, forgotten into the void in linux. 

# Embed one command in another

	Example:

	$ cp $(find . -name "A") ./target_folder/ 

	
# Find files with certain name and copy
	
	$ find . -name "*.pdf" -exec cp {} ./dest_folder \

# Find folders with certain name and remove

	$ rm -rf $(find . -type d -name ".git") 

# Find file with wildcard pattern matching
	
	$ find . -name "[1-9]_*"
	
	$ find . -name "*[A-Z][1-9]_*"

# Fina name in directory with maximal depth

	$ find . -name "<name>" -maxdepth <maxdepth>

# Find keyword in files 

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

# Open a directory in GUI 

	$ nautilus <dir>

# List all available UART serial ports

	$ ls /dev/tty*

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

	"/etc" : "edit text configurations" Human readable text files for system-wide configurations. 

	"/home" : A base directory that contains all the regular users' files.

	"/media" : Used for automatic mounting of removable media such as USB drives, external hard disks, etc. 

	"/mnt" : "mount." Used for manually mounting of removable medias as USB drives, external hard disks, etc.

	"/opt" : "optionals." This is not essential to the OS. It is used to install third-party/user software and programs. 

	 
# Run command at OS startup 

	sudo crontab -e

# Unmount USB mount point

	umount /media/<mount_point>

	rm /media/<mount_point>

# Mount a USB

	mkdir /media/<mount_point>

	mount /dev/<usb_device> /media/<mount_point>

# Create multiple files with same extension

	touch {<file_A>,<file_B>}.<extension>
# Commands Table
| Function                                  | Command Name                | Installation                                 | Common Usage                     |
| ----------------------------------------- | --------------              | ----------------------------------           | -----------                      |
| interactive network manager in terminal   | nmtui                       | sudo apt install network_manager             | sudo nmtui                       |
| hide ubuntu desktop icons                 | gnome-shell-extension-prefs | sudo apt install gnome-shell-extension-prefs | gnome-shell-extension-prefs      |
