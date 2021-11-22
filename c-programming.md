
copy string to buffer
[x] char * a = "abc"
[v] strncpy(buf, "abc", LENGTH);

function that involves copying string should be void.
	void strn_manipulation(char* str)

----

	Format/copying string
	sprintf("buf", "%d", 123);

----
String concatenation

char * strcat ( char * destination, const char * source );

---- 

Disemble a string into muliple strings
buf = "<method> <uri> <versio>" = "GET www.google.com 11.1"

sscanf(buf, "%s %s %s", method, uri, version);

then method = "GET"
		uri = "www.google.com"
		version = "11.1"




