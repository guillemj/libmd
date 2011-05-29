## Process this file with automake to produce Makefile.in

AM_CPPFLAGS = \
	-I$(top_srcdir)/include \
	-include $(top_builddir)/config.h

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = \
	libmd.pc \
	$(nil)

lib_LTLIBRARIES = libmd.la

libmd_la_helper_sources = \
	md2hl.c \
	md4hl.c \
	md5hl.c \
	rmd160hl.c \
	sha1hl.c \
	sha256hl.c \
	sha384hl.c \
	sha512hl.c \
	$(nil)

libmd_la_LDFLAGS = \
	-Wl,--version-script=$(srcdir)/libmd.map \
	-version-number $(LIBMD_ABI)
libmd_la_DEPENDENCIES = \
	libmd.map \
	helper.c \
	$(nil)
libmd_la_SOURCES = \
	md2.c \
	md4.c \
	md5.c \
	rmd160.c \
	sha1.c \
	sha2.c \
	$(libmd_la_helper_sources) \
	$(nil)

BUILT_SOURCES = \
	$(libmd_la_helper_sources) \
	$(nil)

EXTRA_DIST = \
	libmd.map \
	libmd.pc.in \
	helper.c \
	$(nil)

CLEANFILES = \
	$(libmd_la_helper_sources) \
	$(nil)

md2hl.c: helper.c
	$(AM_V_GEN) sed -e 's/hashinc/md2.h/g' -e 's/HASH/MD2/g' $< > $@

md4hl.c: helper.c
	$(AM_V_GEN) sed -e 's/hashinc/md4.h/g' -e 's/HASH/MD4/g' $< > $@

md5hl.c: helper.c
	$(AM_V_GEN) sed -e 's/hashinc/md5.h/g' -e 's/HASH/MD5/g' $< > $@

rmd160hl.c: helper.c
	$(AM_V_GEN) sed -e 's/hashinc/rmd160.h/g' -e 's/HASH/RMD160/g' $< > $@

sha1hl.c: helper.c
	$(AM_V_GEN) sed -e 's/hashinc/sha1.h/g' -e 's/HASH/SHA1/g' $< > $@

sha256hl.c: helper.c
	$(AM_V_GEN) sed -e 's/hashinc/sha2.h/g' -e 's/HASH/SHA256/g' \
	                -e 's/SHA[0-9][0-9][0-9]_CTX/SHA2_CTX/g' $< > $@

sha384hl.c: helper.c
	$(AM_V_GEN) sed -e 's/hashinc/sha2.h/g' -e 's/HASH/SHA384/g' \
	                -e 's/SHA[0-9][0-9][0-9]_CTX/SHA2_CTX/g' $< > $@

sha512hl.c: helper.c
	$(AM_V_GEN) sed -e 's/hashinc/sha2.h/g' -e 's/HASH/SHA512/g' \
	                -e 's/SHA[0-9][0-9][0-9]_CTX/SHA2_CTX/g' $< > $@

runtimelibdir = $(libdir)

install-exec-hook:
	if [ "$(libdir)" != "$(runtimelibdir)" ]; then \
		$(MKDIR_P) $(DESTDIR)$(runtimelibdir); \
		mv $(DESTDIR)$(libdir)/libmd*.so.* \
		   $(DESTDIR)$(runtimelibdir)/; \
		soname=`readlink $(DESTDIR)$(libdir)/libmd.so`; \
		sorelprefix=`echo $(libdir) | sed -r -e 's:(^/)?[^/]+:..:g'`; \
		ln -sf $$sorelprefix$(runtimelibdir)/$$soname \
		       $(DESTDIR)$(libdir)/libmd.so; \
	fi

uninstall-hook:
	rm -f $(DESTDIR)$(runtimelibdir)/libmd*.so*