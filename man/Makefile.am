EXTRA_DIST = \
	mdX.3 \
	$(nil)

CLEANFILES = \
	md4.3 \
	md5.3 \
	$(nil)

SED_MD2_SUBST = -e 's/mdX/md2/g' -e 's/MDX/MD2/g'
SED_MD4_SUBST = -e 's/mdX/md4/g' -e 's/MDX/MD4/g'
SED_MD5_SUBST = -e 's/mdX/md5/g' -e 's/MDX/MD5/g'

md2.3: $(srcdir)/mdX.3
	$(AM_V_GEN) $(SED) $(SED_MD2_SUBST) $(srcdir)/mdX.3 >$@

md4.3: $(srcdir)/mdX.3
	$(AM_V_GEN) $(SED) $(SED_MD4_SUBST) $(srcdir)/mdX.3 >$@

md5.3: $(srcdir)/mdX.3
	$(AM_V_GEN) $(SED) $(SED_MD5_SUBST) $(srcdir)/mdX.3 >$@

dist_man_MANS = \
	md2.3 \
	md4.3 \
	md5.3 \
	rmd160.3 \
	sha1.3 \
	sha2.3 \
	$(nil)

md2_FUNCS = \
	MD2Transform \
	MD2Init \
	MD2Final \
	MD2Update \
	MD2End \
	MD2File \
	MD2FileChunk \
	MD2Data \
	$(nil)

$(md2_FUNCS): md2.3
	$(LN_S) -f md2.3 $(DESTDIR)$(man3dir)/$@.3

md4_FUNCS = \
	MD4Transform \
	MD4Init \
	MD4Final \
	MD4Update \
	MD4End \
	MD4File \
	MD4FileChunk \
	MD4Pad \
	MD4Data \
	$(nil)

$(md4_FUNCS): md4.3
	$(LN_S) -f md4.3 $(DESTDIR)$(man3dir)/$@.3

md5_FUNCS = \
	MD5Transform \
	MD5Init \
	MD5Final \
	MD5Update \
	MD5End \
	MD5File \
	MD5FileChunk \
	MD5Pad \
	MD5Data \
	$(nil)

$(md5_FUNCS): md5.3
	$(LN_S) -f md5.3 $(DESTDIR)$(man3dir)/$@.3

rmd160_FUNCS = \
	RMD160Transform \
	RMD160Init \
	RMD160Final \
	RMD160Update \
	RMD160End \
	RMD160File \
	RMD160FileChunk \
	RMD160Pad \
	RMD160Data \
	$(nil)

$(rmd160_FUNCS): rmd160.3
	$(LN_S) -f rmd160.3 $(DESTDIR)$(man3dir)/$@.3

sha1_FUNCS = \
	SHA1Transform \
	SHA1Init \
	SHA1Final \
	SHA1Update \
	SHA1End \
	SHA1File \
	SHA1FileChunk \
	SHA1Pad \
	SHA1Data \
	$(nil)

$(sha1_FUNCS): sha1.3
	$(LN_S) -f sha1.3 $(DESTDIR)$(man3dir)/$@.3

sha2_FUNCS = \
	SHA256Init \
	SHA256Update \
	SHA256Pad \
	SHA256Final \
	SHA256Transform \
	SHA256End \
	SHA256File \
	SHA256FileChunk \
	SHA256Data \
	SHA384Init \
	SHA384Update \
	SHA384Pad \
	SHA384Final \
	SHA384Transform \
	SHA384End \
	SHA384File \
	SHA384FileChunk \
	SHA384Data \
	SHA512Init \
	SHA512Update \
	SHA512Pad \
	SHA512Final \
	SHA512Transform \
	SHA512End \
	SHA512File \
	SHA512FileChunk \
	SHA512Data \
	$(nil)

$(sha2_FUNCS): sha2.3
	$(LN_S) -f sha2.3 $(DESTDIR)$(man3dir)/$@.3

digest_FUNCS = \
	$(md2_FUNCS) \
	$(md4_FUNCS) \
	$(md5_FUNCS) \
	$(rmd160_FUNCS) \
	$(sha1_FUNCS) \
	$(sha2_FUNCS) \
	$(nil)

install-data-hook: $(digest_FUNCS)
