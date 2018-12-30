
# gnu make

CC=gcc
CFLAGS+=-Wall -Wno-missing-braces -Wno-parentheses -Wno-switch -O2 -g -c -I. 
#-DNOPLAN9DEFINES
O=o
AR=ar
ARFLAGS=rvc
NAN=nan64.$O
NAN=nan64.$O

PREFIX=/usr/local

NUKEFILES=

TGZFILES=

CLEANFILES=

TARG=mk
VERSION=2.0
PORTPLACE=devel/mk
NAME=mk
CLEANFILES=mk mk.1a

OFILES=\
	arc.$O\
	archive.$O\
	bufblock.$O\
	env.$O\
	file.$O\
	graph.$O\
	job.$O\
	lex.$O\
	main.$O\
	match.$O\
	mk.$O\
	parse.$O\
	recipe.$O\
	rc.$O\
	rule.$O\
	run.$O\
	sh.$O\
	shell.$O\
	shprint.$O\
	symtab.$O\
	var.$O\
	varsub.$O\
	word.$O\
	unix.$O

HFILES=\
	mk.h\
	fns.h

all: $(TARG)

install: $(TARG)
	mkdir -p $(PREFIX)/bin
	install -m 0755 mk $(PREFIX)/bin/mk
	cat mk.1 | sed 's;DOCPREFIX;$(PREFIX);g' >mk.1a
	mkdir -p $(PREFIX)/man/man1
	install -m 0644 mk.1a $(PREFIX)/man/man1/mk.1

$(LIB): $(OFILES)
	$(AR) $(ARFLAGS) $(LIB) $(OFILES)

NUKEFILES+=$(LIB)
.c.$O:
	$(CC) $(CFLAGS)  -I../lib/libutf -I../lib/libfmt -I../lib/libbio -I../lib/libregexp -I$(PREFIX)/include $*.c -c

%.$O: %.c
	$(CC) $(CFLAGS) -I ../include -I../lib/libutf -I../lib/libfmt -I../lib/libbio -I../lib/libregexp -I$(PREFIX)/include $*.c -c


$(OFILES): $(HFILES)

clean:
	rm -f $(OFILES) $(LIB) $(CLEANFILES)

nuke:
	rm -f $(OFILES) *.tgz *.rpm $(NUKEFILES)

PORTDIR=/usr/ports/$(PORTPLACE)

ports:
	make tgz
	rm -rf $(PORTDIR)
	mkdir $(PORTDIR)
	cp $(NAME)-$(VERSION).tgz /usr/ports/distfiles
	cat bundle.ports | (cd $(PORTDIR) && awk '$$1=="---" && $$3=="---" { ofile=$$2; next} {if(ofile) print >ofile}')
	(cd $(PORTDIR); make makesum)
	(cd $(PORTDIR); make)
	(cd $(PORTDIR); /usr/local/bin/portlint)
	rm -rf $(PORTDIR)/work
	shar `find $(PORTDIR)` > ports.shar
	(cd $(PORTDIR); tar cf - *) | gzip >$(NAME)-$(VERSION)-ports.tgz
	scp *.tgz rsc@amsterdam.lcs.mit.edu:public_html/software

.phony: all clean nuke install tgz rpm ports

$(TARG): $(OFILES)
	#$(CC) -o $(TARG) $(OFILES) -L$(PREFIX)/lib -L../libutf -L../libfmt -L../libbio -L../libregexp -lregexp9 -lbio -lfmt -lutf
	$(CC) -o $(TARG) $(OFILES) -L$(PREFIX)/lib   -L ../.lib -lbio -lfmt -lutf -lregexp9

