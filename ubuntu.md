# startup scripts 
	$ vim /etc/profile
# A list of good softwares
	vim-gtk3

# Switch between screens.
	Ctrl + Alt + PgUp/PgDn

# Search 
	/

# Open terminal
	Ctrl + Alt + T

# Add a new tab
	Ctrl + Shift + T

# Go to previous tab (buffer)
	Ctrl + PageUp 

	= Ctrl + Fn + UpArrow

# Go to next tab (buffer)
	Ctrl + PageDown

	= Ctrl + Fn + DownArrow

# Make script clickable
	$ sudo vim ~/.local/share/applications/<name>.desktop

	# In the file"

	[Desktop Entry]
	Type=Application
	Terminal=true
	Name=<name>
	Icon=<picture-directory>
	Exec=<script-directory>

# Mapping keys
	$ xmodmap -pke > .Xmodmap

