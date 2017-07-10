
include_HEADERS = include/maxminddb.h

nodist_include_HEADERS = include/maxminddb_config.h

SUBDIRS = \
  src     \
  bin

if TESTS
SUBDIRS += \
  t
endif

EXTRA_DIST = doc t Changes.md LICENSE NOTICE README.md projects/VS12 projects/VS12-tests
dist-hook:
	find $(distdir) -name '.git*' | xargs rm -fr

safedist: clean dist
	tmpdir="$${TMPDIR-/tmp}/safedist-$$$$" \
	  && mkdir "$$tmpdir" \
	  && tar -xvf $(distdir).tar.gz --directory "$$tmpdir" \
	  && $(am__cd) "$$tmpdir/$(distdir)" \
	  && ./configure \
	  && make -j 4 check

