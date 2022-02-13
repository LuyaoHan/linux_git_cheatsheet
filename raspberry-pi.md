# Remote desktop (Raspbian)
	1) Enable VNC and SSH. 
		$ sudo raspi-config

	 	# Select 'Interface Options'

		# Enable VNC and SSH in the config menu.

	2) Install the vnc server.

		$ sudo apt install tightvncserver


	3) Make a new desktop.

		$ tightvncserver

		# Set up passwords accordingly.

	To access this VNC server from another computer.
	1) Find out the ip address of the raspberry pi 

		$ ip addr

		See the inet xxx.xxx.xxx.xxx under 'wlan0' (typically)

	2) On another computer, install vnc viewer. When prompted the connection ip addresses, enter <raspberry-pi-ip-address>:1

