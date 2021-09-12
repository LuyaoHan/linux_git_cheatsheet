# Show line number

	:set number

# Goto top 

	gg

# (Shift) Goto bottom

	<Shift> + g

# Go to <line_number>

	<line_number> + gg

# Autocomplete a commandi for some type
	
	: <Ctrl> + d

	availble options and parameters should pop up; it will be the best way to find mnemonics for a specific command.

# General search
	
	:?text

# Scroll Page Up/Down slowly (Extra-line / Yester-line)

	<Ctrl> + e

	<Ctrl> + y

# Scroll Page Up/Down Quickly

	<Shift> + Up

	<Shift> + Down

# Navegate cursor (Extra / Back)

	Forward: e

	Backward: b

# Move Cursor
	
	Up: k

	Down: j

	Left: h

	Right: l

# Search for a specific <keyword>

	:s/<keyword>

# Search this line and substitute
	
	:s/search_text/sub_text/g

# Search and subtitute globally
	
	:%s/search_text/sub_text/g

# Search and substitute globally with yes/no choice
	
	:%s/search_text/sub_text/gc

# Delete all line with <keyword>

	:g/<keyword>/dd

# Delete all empty lines

	:g/^$/d

# Highlight searched texts
	
	:set hlsearch

# Right-Tab (visual mode) selected lines
	
	:v 
	>>

# List files in current directory

	:e .

	:edit .

	:Explore

# Open a specific file in a new tab

	:b <file>

# Toggle to the next opened tab (go-tab)

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

# Increase current font/window size

	<Ctrl> + <Shift> + <+>

# Decrease current font/window size 

	<Ctrl> + <->
	
# Open all filers in current older in new tabs
	
	:argadd *.sv | tab all
	:argadd *.cpp | tab all

# Enter visual mode (to copy text)
	
	v

# Select column
	
	<Ctrl> + v to enter column select mode

# Edit column 

	1. <Ctrl> + v to enter Visual Block Mode (for column select)

	2. <Shift> + i to enter Insert Mode 

    3. Type in desired text. Note it's normal at the time of typing only ONE row is changed and showed.

	4. <Esc> to apply change to the other rows

# Autocomplete in INSERT mode
	
	<Ctrl> + n

# Autocomplete a command

	:<Ctrl> + d

# Delete line
	
	dd

# Cut line (to the clipvoard)

	cc

# Yank (copy) line

	yy

	<Shift> + y

# Copy to OS (outside of vim) clipboard

	"+y

# Paste from OS (ourside of vim) clipboard 

	"+p

# Undo edit

	u

# Redo edit

	<Ctrl> + r	

# Use vim as a diff-checker

	$ vim -d <file1> <file2>

# Set tab equal to N spaces 

	:set tabstop=<N>

# Show line number

	:set number

# Go to line number

	1. <line_number>

	2. <Shift> + g


# Display Current file director and line numbery

	1 + <Ctrl> + g

# Open <file> in a new tab

	:tabedit <file>
	
	:tabnew <file>

# Save current edit as another file

	:w <file_name>

# Open terminal in a new window

	:ter

	:terminal

# Open terminal in a bottom window

	:bo term

# Open file explorer in a vertial split
	
	:Vexplore

# Resize window when having on a horizontal split. (several horizontal windows)

	:resize +<num>
	:resize -<num>

# Resize window when having a vertical split. (several vertical windows)

	:vertical resize +<num>
	:vertical resize -<num>

# Swap the position of two splited window

	:<Ctrl+w> <Ctrl+r>


