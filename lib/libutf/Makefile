# gnu make

# The only goal here is to generate a static lib (.a) to link into the mk binary

CC=gcc
CFLAGS+=-Wall -Wno-missing-braces -Wno-parentheses -Wno-switch -O2 -g -c -I.
O=o
AR=ar
ARFLAGS=rvc
NAN=nan64.$O    # default, can be overriden by Make.$(SYSNAME)
NAN=nan64.$O

PREFIX=/usr/local

LIB=libutf.a
VERSION=2.0
PORTPLACE=devel/libutf
NAME=libutf

OFILES=\
	rune.$O\
	runestrcat.$O\
	runestrchr.$O\
	runestrcmp.$O\
	runestrcpy.$O\
	runestrdup.$O\
	runestrlen.$O\
	runestrecpy.$O\
	runestrncat.$O\
	runestrncmp.$O\
	runestrncpy.$O\
	runestrrchr.$O\
	runestrstr.$O\
	runetype.$O\
	utfecpy.$O\
	utflen.$O\
	utfnlen.$O\
	utfrrune.$O\
	utfrune.$O\
	utfutf.$O

HFILES=\
	utf.h

all: $(LIB)

install: $(LIB)
	cp *.a ../../.lib/

$(LIB): $(OFILES)
	$(AR) $(ARFLAGS) $(LIB) $(OFILES)

NUKEFILES+=$(LIB)
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
