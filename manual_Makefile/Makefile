package = jupiter
version = 1.0
tarname = $(package)
distdir = $(tarname)-$(version)

prefix = /usr/local
exec_prefix = $(prefix)
bindir = $(exec_prefix)/bin
export prefix exec_prefix bindir

all clean check install uninstall jupiter:
	$(MAKE) -C src $@

dist: $(distdir).tar.gz

$(distdir).tar.gz: FORCE $(distdir)
	tar chof - $(distdir) |\
		gzip -9 -c > $(distdir).tar.gz
	rm -rf $(distdir)

$(distdir):
	mkdir -p $(distdir)/src
	cp Makefile $(distdir)
	cp src/Makefile $(distdir)/src
	cp src/main.c $(distdir)/src

distcheck: $(distdir).tar.gz
	gzip -cd $+ | tar xvf -
	$(MAKE) -C $(distdir) all check clean
	rm -rf $(distdir)
	@echo "** Package $(distdir).tar.gz\
		ready for distribution."

.PHONY: FORCE all clean check dist distcheck
.PHONY: install uninstall

FORCE:
	-rm $(distdir).tar.gz &> /dev/null
	-rm -rf $(distdir) &> /dev/null

