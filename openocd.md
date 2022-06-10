# Setup environment

	$ sudo apt install openocd

# Following example, target board is STM32F401RE Nucleo Board, Host Ubuntu 18.04

	To make sure st-link is detected

	$ st-info --probe
	>
		Found 1 stlink programmers
		version:    V2J33S25
		serial:     066DFF545071494867223048
		flash:      524288 (pagesize: 16384)
		sram:       98304
		chipid:     0x0433
		descr:      F4xx (Dynamic Efficency)

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
		[EMPTY LINES]

	This will start an openocd server, in order to use command line on OpenOCD server, connect to localhost:

	$ telnet localhost 4444

		Trying 127.0.0.1...
		Connected to localhost.
		Escape character is '^]'.
		Open On-Chip Debugger
	>


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

		Following is log indicating successful writing procedure:

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
		Info : Target voltage: 3.259513
		Info : stm32f4x.cpu: hardware has 6 breakpoints, 4 watchpoints
		Info : Unable to match requested speed 2000 kHz, using 1800 kHz
		Info : Unable to match requested speed 2000 kHz, using 1800 kHz
		adapter speed: 1800 kHz
		target halted due to debug-request, current mode: Thread
		xPSR: 0x01000000 pc: 0x08002810 msp: 0x20018000
		Info : Unable to match requested speed 8000 kHz, using 4000 kHz
		Info : Unable to match requested speed 8000 kHz, using 4000 kHz
		adapter speed: 4000 kHz
		** Programming Started **
		auto erase enabled
		Info : device id = 0x10016433
		Info : flash size = 512kbytes
		target halted due to breakpoint, current mode: Thread
		xPSR: 0x61000000 pc: 0x20000046 msp: 0x20018000
		wrote 16384 bytes from file ./build/nRF24-transmitter.elf in 0.615858s (25.980 KiB/s)
		** Programming Finished **
		** Verify Started **
		target halted due to breakpoint, current mode: Thread
		xPSR: 0x61000000 pc: 0x2000002e msp: 0x20018000
		target halted due to breakpoint, current mode: Thread
		xPSR: 0x61000000 pc: 0x2000002e msp: 0x20018000
		verified 11040 bytes in 0.095395s (113.017 KiB/s)
		** Verified OK **
		** Resetting Target **
		Info : Unable to match requested speed 2000 kHz, using 1800 kHz
		Info : Unable to match requested speed 2000 kHz, using 1800 kHz
		adapter speed: 1800 kHz
		shutdown command invoked


# To use GDB (arm-none-eabi-gdb) with OpenOCD, make sure to start the OpenOCD server first.

		For target board is STM32F401RE Nucleo Board, Host Ubuntu 18.04

		$ sudo openocd -f /usr/share/openocd/scripts/interface/stlink-v2-1.cfg -f /usr/share/openocd/scripts/target/stm32f4x.cfg

		In another window

		$ arm-none-eabi-gdb main.elf

		(gdb) > target remote localhost:3333

		Remote debugging using localhost:3333
		0x00000000 in ?? ()

		/* monitor means that the proceeding commands are for debugger program, in this case, OpenOCD. */
		(gdb) monitor reset halt
		Unable to match requested speed 2000 kHz, using 1800 kHz
		Unable to match requested speed 2000 kHz, using 1800 kHz
		adapter speed: 1800 kHz
		target halted due to debug-request, current mode: Thread 
		xPSR: 0x01000000 pc: 0x080028b8 msp: 0x20018000

		(!) We must use load before (gdb)continue! Only that it can start run the program normally.
		(gdb) load
		Loading section .isr_vector, size 0x194 lma 0x8000000
		Loading section .text, size 0x2a74 lma 0x80001c0
		Loading section .rodata, size 0x2c8 lma 0x8002c34
		Loading section .ARM, size 0x8 lma 0x8002efc
		Loading section .init_array, size 0x4 lma 0x8002f04
		Loading section .fini_array, size 0x4 lma 0x8002f08
		Loading section .data, size 0x70 lma 0x8002f0c
		Start address 0x08002bc8, load size 12112
		Transfer rate: 16 KB/sec, 1730 bytes/write.


# embedded GDB programs 

		list
		(gdb) l 

		continue
		(gdb) c 

		break, add breakpoint
		(gdb) b

		information, display informaion about breakpoint
		(gdb) i b

		step (in / next)
		(gdb) s 

		finish, essentially run until the end of current function.
		(gdb) finish 

		next 
		(gdb) n

		until line xxx
		(gdb) u

		print 
		(gdb) p

		print hex 
		(gdb) p/x <variable>

		display traced variable
		(gdb) display

		back-trace
		(gdb) bt

		quit
		(gdb) q

		enter GUI
		(gdb) - 

		switch to assembly layout
		(gdb) layout asm

		generate core dump
		(gdb) generate-core-file
    > Saved corefile ...
		








			



			



