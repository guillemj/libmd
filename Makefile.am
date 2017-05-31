## Process this file with automake to produce Makefile.in

SUBDIRS = include man src test

ACLOCAL_AMFLAGS = -I m4

EXTRA_DIST = \
	autogen \
	get-version \
	m4/libmd-linker.m4 \
	$(nil)

dist-hook:
	echo $(VERSION) >$(distdir)/.dist-version
	if [ -d .git ]; then \
	  XDG_CONFIG_HOME= HOME= git log --stat -C >$(distdir)/ChangeLog; \
	fi
