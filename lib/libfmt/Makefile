
# gnu make

# The only goal here is to generate a static lib (.a) to link into the mk binary

CC=gcc
CFLAGS+=-Wall -Wno-missing-braces -Wno-parentheses -Wno-switch -O2 -g -c -I.
O=o
AR=ar
ARFLAGS=rvc
NAN=nan64.$O    # default, can be overriden by Make.$(SYSNAME)
NAN=nan64.$O

LIB=libfmt.a
VERSION=2.0
PORTPLACE=devel/libfmt
NAME=libfmt

NUM=\
	charstod.$O\
	pow10.$O

OFILES=\
	dofmt.$O\
	dorfmt.$O\
	errfmt.$O\
	fltfmt.$O\
	fmt.$O\
	fmtfd.$O\
	fmtfdflush.$O\
	fmtlock.$O\
	fmtprint.$O\
	fmtquote.$O\
	fmtrune.$O\
	fmtstr.$O\
	fmtvprint.$O\
	fprint.$O\
	print.$O\
	runefmtstr.$O\
	runeseprint.$O\
	runesmprint.$O\
	runesnprint.$O\
	runesprint.$O\
	runevseprint.$O\
	runevsmprint.$O\
	runevsnprint.$O\
	seprint.$O\
	smprint.$O\
	snprint.$O\
	sprint.$O\
	strtod.$O\
	vfprint.$O\
	vseprint.$O\
	vsmprint.$O\
	vsnprint.$O\
	$(NUM)\
	$(NAN)

HFILES=\
	fmtdef.h\
	fmt.h

all: $(LIB)

install: $(LIB)
	cp *.a ../../.lib/

$(NAN).$O: nan.h
strtod.$O: nan.h

test: $(LIB) test.$O
	$(CC) -o test test.$O $(LIB) -L$(PREFIX)/lib -lutf

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
