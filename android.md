#### Set up TCP connection between Android and PC (Ubuntu20.04)

> $adb usb

> $adb tcpip 5555

> $adb connect 172.26.37.208:5555

#### ssh to Termux(Android Teminal) from terminal
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


