# Set up TCP connection between Android and PC (Ubuntu20.04)

> $adb usb

> $adb tcpip 5555

> $adb connect 172.26.37.208:5555

# Install apk through adb

	(!) Make sure adb debug is on

	$ adb install <package>.apk

# ssh to Termux(Android Teminal) from terminal
> Make sure phone is rooted

> Install termux on the phone from the Google App Store

> Install OpenSSH
	
	$ pkg upgrade

	$ pkg install openssh

> Setup a password if it has not been setup before

	$ passwd 

> Find username of the Android

	$ whoami

> Find the ip address of Android 

	$ifconfig

	Identify the ip address. Example: inet xxx.xxx.xxx.x

> Start the ssh server in linux

	$ sshd

> Verify that it's running

	$ logcat -s 'ssh:*'

> ssh from PC terminal

	$ ssh <username>@<host_ip_address> -p 8022

# List name of application packages:
adb shell pm list packages -f

# Open application 
adb shell monkey -p <app.package.name> 1

# Tap screen location
adb shell input tap <x> <y>

# Transfer file to the android device
adb push <file_to_transfer> <target_location>

# Delete file on the android device
adb shell rm -f <target_location>

# ADB without USB cable

	In Termux:
	
	su
	setprop service.adb.tcp.port 5555
	stop adbd
	start adbd
	ifconfig # find the ipv4 address

	In PC terminal:
	
	adb tcpip 5555
	adb connect <ip_address>:5555

# Example:
adb shell monkey -p com.instagram.android 1
adb shell input tap 480 118
adb shell input tap 680 120
adb shell input tap 680 120
adb shell input tap 220 256
adb shell input text "California Sunset, 2021 Summer"
(adb shell input keyevent 62 # space)
adb shell input tap 680 120
