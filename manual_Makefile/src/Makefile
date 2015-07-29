CC     = gcc
CFLAGS = -g -O2

all: jupiter

jupiter: main.c
	$(CC) $(CFLAGS) $(CPPFLAGS) -o $@ $+

clean:
	-rm jupiter

check: all
	./jupiter |grep "Hello from .*jupiter!"
	@echo "** ALL TESTS PASSED ***"

install:
	mkdir -p $(DESTDIR)$(bindir)
	install -m 0755 jupiter $(DESTDIR)$(bindir)

uninstall:
	-rm $(DESTDIR)$(bindir)/jupiter

.PONY: all clean check install uninstall

