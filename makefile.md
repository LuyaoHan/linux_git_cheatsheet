# Log executed command by make file to terminal. This does not execute the actual compilation.
  $ make -n

# Wild-card select example
	LVGL_CORE=$(wildcard src/lvgl/src/core/*.c) \
	$(wildcard src/lvgl/src/hal/*.c) \
	$(wildcard src/lvgl/src/draw/*.c) \
	...

	$(wildcard src/lvgl/src/extra/*.c) 

# Change filenames from *.c to *.o
	LVGL_OBJ=$(patsubst %.c, %.o, $(LVGL_CORE))


