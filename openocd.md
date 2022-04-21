# Setup environment

	$ sudo apt install openocd

# Target board is STM32F401RE Nucleo Board, Host Ubuntu 18.04

	The configuration files specifies the SWD interface and the target board.

	$	sudo openocd -f /usr/share/openocd/scripts/interface/stlink-v2-1.cfg -f /usr/share/openocd/scripts/target/stm32f4x.cfg

	(!) If it shows waning on device ID, not recognized as a STM32 family. It's probably because we have selected the wrong cfg file.

	Expected output:
		>
		Open On-Chip Debugger 0.10.0
		Licensed under GNU GPL v2
		For bug reports, read
			http://openocd.org/doc/doxygen/bugs.html
		Info : auto-selecting first available session transport "hla_swd". To override use 'transport select <transport>'.
		Info : The selected transport took over low-level target control. The results might differ compared to plain JTAG/SWD
		adapter speed: 2000 kHz
		adapter_nsrst_delay: 100
		none separate
		Info : Unable to match requested speed 2000 kHz, using 1800 kHz
		Info : Unable to match requested speed 2000 kHz, using 1800 kHz
		Info : clock speed 1800 kHz
		Info : STLINK v2 JTAG v33 API v2 SWIM v25 VID 0x0483 PID 0x374B
		Info : using stlink api v2
		Info : Target voltage: 3.248915
		Info : stm32f4x.cpu: hardware has 6 breakpoints, 4 watchpoints



	This will start an openocd terminal, in order to open that terminal:

	$ telnet localhost 4444

	> reset halt                             
		Unable to match requested speed 2000 kHz, using 1800 kHz
		Unable to match requested speed 2000 kHz, using 1800 kHz
		adapter speed: 1800 kHz
		target halted due to debug-request, current mode: Thread 
		xPSR: 0x01000000 pc: 0x08002004 msp: 0x20018000
	> flash erase_sector 0 0 last
		erased sectors 0 through 7 on flash bank 0 in 8.974339s
	> flash write_image nRF24-transmitter.elf
		target halted due to breakpoint, current mode: Thread 
		xPSR: 0x61000000 pc: 0x20000046 msp: 0x20018000
		wrote 8572 bytes from file nRF24-transmitter.elf in 0.199320s (41.998 KiB/s)
	> reset
		Unable to match requested speed 2000 kHz, using 1800 kHz
		Unable to match requested speed 2000 kHz, using 1800 kHz
		adapter speed: 1800 kHz

# The above process is complicated, involves a lot of steps, this can be condensed to one command:

		$ sudo openocd -f /usr/share/openocd/scripts/interface/stlink-v2-1.cfg -f /usr/share/openocd/scripts/target/stm32f4x.cfg -c 'program ./build/nRF24-transmitter.elf verify reset exit'




	



	



