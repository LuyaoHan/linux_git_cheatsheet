$ gdb
(gdb) file <executable>
(gdb) p <variable>
(gdb) p/x <variable>

# Enter gdb
$ gdb

# Load a flie / executable
(gdb) file main

# Print binary
(gdb) p/t <variable>

(gdb) !ls
(gdb) !make

# Send special commands to gdb-server (usually hardware dependent) 
(gdb) monitor tpiu config, etc.

# Apply to all threads, print backtrace
(gdb) thread apply all bt

# Print backtrace
(gdb) bt

# Open gdb for MCU
(gdb) gdb-multiarch

# Connect to remote target
(gdb) target remote localhost:3333

# Delete all breakpoints
(gdb) delete

# Delete certain breakpoints
(gdb) delete <N>
Delete all breakpoints? (y or n) y


