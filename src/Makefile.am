# Copyright (c) 2014, Facebook, Inc.
# All rights reserved.
# This source code is licensed under the BSD-style license found in the
# LICENSE file in the root directory of this source tree. An additional grant
# of patent rights can be found in the PATENTS file in the same directory.

AUTOMAKE_OPTIONS = foreign
CFLAGS += -Wall

lib_LTLIBRARIES = liblogfaf.la
liblogfaf_la_SOURCES = liblogfaf.c

liblogfaf_la_LIBADD=@DL_LDLIBS@

nodist_bin_SCRIPTS = logfaf
dist_noinst_DATA = logfaf.in
DISTCLEANFILES = logfaf

logfaf:: Makefile $(srcdir)/logfaf.in
	rm -f $(srcdir)/logfaf.tmp $(srcdir)/logfaf && \
	$(SED) -e 's|@libdir\@|$(libdir)|g' $(srcdir)/logfaf.in > \
	$(srcdir)/logfaf.tmp && mv $(srcdir)/logfaf.tmp $(srcdir)/logfaf
