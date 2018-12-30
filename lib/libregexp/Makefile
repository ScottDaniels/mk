
# gnu make

# The only goal here is to generate a static lib (.a) to link into the mk binary

CC=gcc
C_FLAGS+=-Wall -Wno-missing-braces -Wno-parentheses -Wno-switch -O2 -g -c -I. 
#-DNOPLAN9DEFINES
O=o
AR=ar
ARFLAGS=rvc
NAN=nan64.$O    # default, can be overriden by Make.$(SYSNAME)
NAN=nan64.$O

PREFIX=/usr/local

LIB=libregexp9.a
VERSION=2.0
PORTPLACE=devel/libregexp9
NAME=libregexp9

OFILES=\
	regcomp.$O\
	regerror.$O\
	regexec.$O\
	regsub.$O\
	regaux.$O\
	rregexec.$O\
	rregsub.$O

HFILES=\
	regexp9.h\
	regcomp.h

all: $(LIB)

install: $(LIB)
	cp *.a ../../.lib/

test: test.$O $(LIB)
	$(CC) -o test test.$O $(LIB) -L/usr/local/lib -lfmt -lutf

test2: test2.$O $(LIB)
	$(CC) -o test2 test2.$O $(LIB) -L/usr/local/lib -lfmt -lutf

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
