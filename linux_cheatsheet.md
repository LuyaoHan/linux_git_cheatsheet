# (!)When computer frozen (Ubuntu 20.04)
	
	1. press <Alt> + <Print Screen> keys
	2. release  <Print Screen>
	3. type r-s-i-s-u-b

# Run program in the background while surpressing output

	$ ./program &>/dev/null &

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

# List all files except for names that included certain keywords
	
	$ ls - I "name"

# List file size in MB
	
	$ ls -al --block-size=M

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

	".tar.gz" is the same as ".tgz"

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
