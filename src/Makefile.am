## Process this file with automake to produce Makefile.in

AM_CPPFLAGS = \
	-I$(top_builddir) \
	-I$(srcdir) \
	-I$(top_srcdir)/include \
	$(nil)

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

EXTRA_libmd_la_DEPENDENCIES = \
	libmd.map

libmd_la_LDFLAGS = \
	-no-undefined \
	-version-number $(LIBMD_ABI)
if HAVE_LINKER_VERSION_SCRIPT
libmd_la_LDFLAGS += \
	-Wl,--version-script=$(srcdir)/libmd.map
else
libmd_la_LDFLAGS += \
	-export-symbols libmd.sym
EXTRA_libmd_la_DEPENDENCIES += \
	libmd.sym
endif
EXTRA_libmd_la_DEPENDENCIES += \
	helper.c \
	$(nil)
libmd_la_SOURCES = \
	local-link.h \
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

DISTCLEANFILES = \
	libmd.sym \
	$(nil)

# Generate a simple libtool symbol export list to be used as a fallback if
# there is no version script support.
libmd.sym: libmd.map
	$(AM_V_GEN) $(SED) -ne 's/^[[:space:]]\{1,\}\([A-Za-z0-9]\{1,\}\);/\1/p' libmd.map > $@

md2hl.c: helper.c
	$(AM_V_GEN) $(SED) -e 's/hashinc/md2.h/g' -e 's/HASH/MD2/g' helper.c > $@

md4hl.c: helper.c
	$(AM_V_GEN) $(SED) -e 's/hashinc/md4.h/g' -e 's/HASH/MD4/g' helper.c > $@

md5hl.c: helper.c
	$(AM_V_GEN) $(SED) -e 's/hashinc/md5.h/g' -e 's/HASH/MD5/g' helper.c > $@

rmd160hl.c: helper.c
	$(AM_V_GEN) $(SED) -e 's/hashinc/rmd160.h/g' -e 's/HASH/RMD160/g' helper.c > $@

sha1hl.c: helper.c
	$(AM_V_GEN) $(SED) -e 's/hashinc/sha1.h/g' -e 's/HASH/SHA1/g' helper.c > $@

sha256hl.c: helper.c
	$(AM_V_GEN) $(SED) -e 's/hashinc/sha2.h/g' -e 's/HASH/SHA256/g' \
	                -e 's/SHA[0-9][0-9][0-9]_CTX/SHA2_CTX/g' helper.c > $@

sha384hl.c: helper.c
	$(AM_V_GEN) $(SED) -e 's/hashinc/sha2.h/g' -e 's/HASH/SHA384/g' \
	                -e 's/SHA[0-9][0-9][0-9]_CTX/SHA2_CTX/g' helper.c > $@

sha512hl.c: helper.c
	$(AM_V_GEN) $(SED) -e 's/hashinc/sha2.h/g' -e 's/HASH/SHA512/g' \
	                -e 's/SHA[0-9][0-9][0-9]_CTX/SHA2_CTX/g' helper.c > $@

runtimelibdir = $(libdir)

install-exec-hook:
	if [ "$(libdir)" != "$(runtimelibdir)" ]; then \
		$(MKDIR_P) $(DESTDIR)$(runtimelibdir); \
		mv $(DESTDIR)$(libdir)/libmd*.so.* \
		   $(DESTDIR)$(runtimelibdir)/; \
		soname=`readlink $(DESTDIR)$(libdir)/libmd.so`; \
		sorelprefix=`echo $(libdir) | $(SED) -r -e 's:(^/)?[^/]+:..:g'`; \
		ln -sf $$sorelprefix$(runtimelibdir)/$$soname \
		       $(DESTDIR)$(libdir)/libmd.so; \
	fi

uninstall-hook:
	rm -f $(DESTDIR)$(runtimelibdir)/libmd*.so*
