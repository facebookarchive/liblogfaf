AUTOMAKE_OPTIONS = foreign
CFLAGS += -Wall

lib_LTLIBRARIES = liblogfaf.la
liblogfaf_la_SOURCES = liblogfaf.c
liblogfaf_la_LIBADD = -ldl

nodist_bin_SCRIPTS = logfaf
dist_noinst_DATA = logfaf.in
DISTCLEANFILES = logfaf

logfaf:: Makefile $(srcdir)/logfaf.in
	rm -f $(srcdir)/logfaf.tmp $(srcdir)/logfaf && \
	$(SED) -e 's|@libdir\@|$(libdir)|g' $(srcdir)/logfaf.in > \
	$(srcdir)/logfaf.tmp && mv $(srcdir)/logfaf.tmp $(srcdir)/logfaf
