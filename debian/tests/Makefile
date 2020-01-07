# libutf8proc Makefile

UCFLAGS = $(shell dpkg-buildflags --get CPPFLAGS) \
	  $(shell dpkg-buildflags --get CFLAGS)

all: check
	  
test/tests.o: test/tests.c test/tests.h utf8proc.h
	$(CC) $(UCFLAGS) -c -o test/tests.o test/tests.c

test/normtest: test/normtest.c test/tests.o  utf8proc.h test/tests.h
	$(CC) $(UCFLAGS) $(LDFLAGS) test/normtest.c test/tests.o -lutf8proc -o $@

test/graphemetest: test/graphemetest.c test/tests.o  utf8proc.h test/tests.h
	$(CC) $(UCFLAGS) $(LDFLAGS) test/graphemetest.c test/tests.o  -lutf8proc -o $@

test/printproperty: test/printproperty.c test/tests.o  utf8proc.h test/tests.h
	$(CC) $(UCFLAGS) $(LDFLAGS) test/printproperty.c test/tests.o  -lutf8proc -o $@

test/charwidth: test/charwidth.c test/tests.o  utf8proc.h test/tests.h
	$(CC) $(UCFLAGS) $(LDFLAGS) test/charwidth.c test/tests.o  -lutf8proc -o $@

test/valid: test/valid.c test/tests.o  utf8proc.h test/tests.h
	$(CC) $(UCFLAGS) $(LDFLAGS) test/valid.c test/tests.o  -lutf8proc -o $@

test/iterate: test/iterate.c test/tests.o  utf8proc.h test/tests.h
	$(CC) $(UCFLAGS) $(LDFLAGS) test/iterate.c test/tests.o  -lutf8proc -o $@

test/case: test/case.c test/tests.o  utf8proc.h test/tests.h
	$(CC) $(UCFLAGS) $(LDFLAGS) test/case.c test/tests.o  -lutf8proc -o $@

test/custom: test/custom.c test/tests.o  utf8proc.h test/tests.h
	$(CC) $(UCFLAGS) $(LDFLAGS) test/custom.c test/tests.o  -lutf8proc -o $@

test/misc: test/misc.c test/tests.o  utf8proc.h test/tests.h
	$(CC) $(UCFLAGS) $(LDFLAGS) -DUNICODE_VERSION='"'`$(PERL) -ne "/^UNICODE_VERSION=/ and print $$';" data/Makefile`'"' test/misc.c test/tests.o  -lutf8proc -o $@

check: test/normtest test/graphemetest test/printproperty test/case test/custom test/charwidth test/misc test/valid test/iterate bench/util.c bench/util.h 
	test/charwidth
	test/valid
	test/iterate
	test/case
	test/custom
