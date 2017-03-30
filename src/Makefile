# Makefile sample

CC=gcc
AR=ar
CFLAGS=-c -g
INCLUDE=-I../inc
LIBS=-L. -lhello
LIBSONAME=libhello.so
LIBTARGET=libhello.so.0.0
#build library name

SRCS=read.c write.c
OBJS=$(SRCS:.c=.o)

.SUFFIXES:.c.o
.c.o:
	$(CC) $(CFLAGS) -fPIC $(INCLUDE) $<

all: test
	
$(LIBTARGET) : $(OBJS)
	$(CC) -g -shared -Wl,-soname,$(LIBSONAME) -o $@ $(OBJS) -lc
	ln -sf $@ $(LIBSONAME)

test: main.o $(LIBTARGET)
	$(CC) -o $@ main.o $(LIBS)
	export LD_LIBRARY_PATH=$PWD
	echo $LD_LIBRARY_PATH
	@echo done

clean:
	rm -rf test *.o $(LIBTARGET)
