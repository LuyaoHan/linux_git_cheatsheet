1. Download source
	
		$ git clone <source-repo>

2. Download cross-compile tool

		$ git clone <tool-repo>

3. Export path of the tool as environment path

		> PATH=$PATH:<path-to-tool>

		Example:

		export PATH=$PATH:/home/luyao/arm-rpi-4.9.3-linux-gnueabihf/bin/arm-linux-gnueabihf-

4. cd to the source file

5. make a configuration file

		$ make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- defconfig

6. make 

		$ make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage modules dtbs -j5


