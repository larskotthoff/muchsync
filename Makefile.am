
ACLOCAL_AMFLAGS = ${ACLOCAL_FLAGS} -I m4
AM_CPPFLAGS = $(sqlite3_CFLAGS) $(libcrypto_CFLAGS) $(xapian_CPPFLAGS)
LDADD = $(sqlite3_LIBS)	$(libcrypto_LIBS) -lnotmuch $(xapian_LIBS)

bin_PROGRAMS = muchsync

muchsync_SOURCES = infinibuf.cc misc.cc muchsync.cc notmuch_db.cc	\
	protocol.cc sqlstmt.cc sql_db.cc xapian_sync.cc cleanup.h	\
	misc.h muchsync.h infinibuf.h notmuch_db.h sqlstmt.h sql_db.h

CLEANFILES = *~
maintainer-clean-local:
	+@echo rm -rf `sed -ne 's!^/!!p' .gitignore` Makefile.in
	rm -rf `sed -ne 's!^/!!p' .gitignore` Makefile.in

muchsync.1: muchsync.1.md
	pandoc -s -w man muchsync.1.md -o muchsync.1

man_MANS = muchsync.1
EXTRA_DIST = muchsync.1.md $(man_MANS)
