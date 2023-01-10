# Remote desktop (Raspbian)
	1) Enable VNC and SSH. 
		$ sudo raspi-config

	 	# Select 'Interface Options'

		# Enable VNC and SSH in the config menu.


	To access this VNC server from another computer.
	1) Find out the ip address of the raspberry pi 

		$ ip addr

		See the inet xxx.xxx.xxx.xxx under 'wlan0' (typically)

	2) On another computer, install vnc viewer (realvnc viewer is preferred). When prompted the connection ip addresses, enter <raspberry-pi-ip-address>

	# The user name will be 'pi' by default

	If you don't know the ip address and are on the same network. Use 'raspberrypi.local' instead of the ip address also works.

# Get pinout

	$ pinout

# VNC with 1920x1080
	vncserver :0 -geometry 1920x1080 -depth 24
