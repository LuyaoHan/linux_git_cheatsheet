# Enable gcov
	In Makefile, add 
	CGOV=-fprofile-arcs -ftest-coverage

# Recompile
	$ make

# Run the executable
	$ make
	$ ./main

# Now run gcov main
	$ gcov main
	> "Lines executed: ... of <TOTAL_LINEs>"
	A file is generated: main.c.gov
	$ vim main.c.gov

	'####' means lines that are not exercised.
