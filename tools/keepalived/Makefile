# Makefile
#
# Keepalived OpenSource project.
#
# Copyright (C) 2001-2011 Alexandre Cassen, <acassen@linux-vs.org>

TARFILES = AUTHOR bin ChangeLog configure configure.in CONTRIBUTORS COPYING \
	   doc genhash INSTALL install-sh keepalived keepalived.spec.in lib Makefile.in \
	   README TODO VERSION

TARBALL = keepalived-1.2.2.tar.gz

all:
	$(MAKE) -C lib || exit 1;
	$(MAKE) -C keepalived
	$(MAKE) -C genhash
	@echo ""
	@echo "Make complete"

debug:
	$(MAKE) -C lib || exit 1;
	$(MAKE) -C keepalived debug
	@echo ""
	@echo "Make complete"

profile:
	$(MAKE) -C lib || exit 1;
	$(MAKE) -C keepalived profile
	@echo ""
	@echo "Make complete"

clean:
	$(MAKE) -C lib clean
	$(MAKE) -C keepalived clean
	$(MAKE) -C genhash clean

distclean:
	$(MAKE) -C lib distclean
	$(MAKE) -C keepalived distclean
	$(MAKE) -C genhash distclean
	rm -f Makefile
	rm -f keepalived.spec

mrproper: distclean
	rm -f config.*

uninstall:
	$(MAKE) -C keepalived uninstall
	$(MAKE) -C genhash uninstall

install:
	$(MAKE) -C keepalived install
	$(MAKE) -C genhash install

tarball: mrproper
	mkdir keepalived-1.2.2
	cp -a $(TARFILES) keepalived-1.2.2
	tar --exclude .git -czf $(TARBALL) keepalived-1.2.2
	rm -rf keepalived-1.2.2

rpm:
	rpmbuild -ba keepalived.spec
