
# gnu make

# The only goal here is to generate a static lib (.a) to link into the mk binary

CC=gcc
CFLAGS+=-Wall -Wno-missing-braces -Wno-parentheses -Wno-switch -O2 -g -c -I.
O=o
AR=ar
ARFLAGS=rvc
NAN=nan64.$O    # default, can be overriden by Make.$(SYSNAME)
NAN=nan64.$O

LIB=libbio.a
VERSION=2.0
NAME=libbio

OFILES=\
	bbuffered.$O\
	bfildes.$O\
	bflush.$O\
	bgetc.$O\
	bgetd.$O\
	bgetrune.$O\
	binit.$O\
	boffset.$O\
	bprint.$O\
	bvprint.$O\
	bputc.$O\
	bputrune.$O\
	brdline.$O\
	brdstr.$O\
	bread.$O\
	bseek.$O\
	bwrite.$O

HFILES=\
	bio.h

all: $(LIB)

install: $(LIB)
	cp *.a ../../.lib/
	

$(LIB): $(OFILES)
	$(AR) $(ARFLAGS) $(LIB) $(OFILES)

NUKEFILES=$(LIB)
.c.$O:
	$(CC) $(C_FLAGS) -I../libutf -I../libfmt -I../libbio -I../libregexp -I$(PREFIX)/include $*.c -c 

%.$O: %.c
	$(CC) $(C_FLAGS) -I../libutf -I../libfmt -I../libbio -I../libregexp -I$(PREFIX)/include $*.c -c


$(OFILES): $(HFILES)

clean:
	rm -f $(OFILES) $(LIB) $(CLEANFILES)

nuke:
	rm -f $(OFILES) *.tgz *.rpm $(NUKEFILES)

.phony: all clean nuke install tgz rpm ports
