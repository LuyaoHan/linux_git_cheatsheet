# General search
	
	:?text

# Scroll Page Up/Down

	<Ctrl> + E

	<Ctrl> + Y

# Move Cursor
	
	Up: k

	Down: j

	Left: h

	Right: l
# Search this line and substitute
	
	:s/search_text/sub_text/g

# Search and subtitute globally
	
	:%s/search_text/sub_text/g

# Search and substitute with yes/no prompt
	
	:%s/search_text/sub_text/gc

# Right-Tab selected lines
	
	:v 
	>>

# List files in current directory

	:e .

	:edit .

# Open a specific file in a new tab

	:b <file>

# Toggle to the next opened tab (of file)

	:gt

# Toggle to the previous opened tab

	:gT

# Split the current window

	horizontal split
	
	:split 

	vertical split

	:vsplit

# Close split window

	<Ctrl> + w,q

# Toggle between split windows 

	<Ctrl> + ww (double tap 'w' )
	
# Open all filers in current older in new tabs
	
	:argadd *.sv | tab all
	:argadd *.cpp | tab all

# Enter visual mode (to copy text)
	
	v

# Select column
	
	<Ctrl> + V to enter column select mode

# Autocomplete
	
	<Ctrl> + N 

# Delete line
	
	dd

# Cut line (to the clipvoard)

	cc

# Yank (copy) line

	yy 

# Copy to OS (outside of vim) clipboard

	"+y

# Paste from OS (ourside of vim) clipboard 

	"+p

# Edit column 

    1. Ctrl + v column mode edit command, select using arrow keys.
    3. Shift + i to go into insert mode in column mode
    4. Type in desired text. Note it's normal at the time of typing only ONE row is changed and showed.
    5. Press the Esc key to apply the changes to the selected column

