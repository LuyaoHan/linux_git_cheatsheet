# Generate three-address code.
	$ arm-none-gnueabi-gcc -fdump-tree-gimple main.c

# Gnerate assembly code
	$ arm-none-gnueabi-objdump -s main.elf

# View linker script
	$ arm-none-eabi-ld --verbose

# Read relocation table 
	$ arm-none-gnueabi-readelf -r main.o

# View program header table from elf.
	$ arm-none-gnueabi-readelf -l a.out

# Get assembly from executable
	$ arm-none-gnueabi-objdump -D main.o > main.S
