# For multiple programs using a single source file each,
# we can just define 'progs' and create custom targets.
PROGS	=	vale-ctl
LIBNETMAP =

CLEANFILES = $(PROGS) *.o

SRCDIR ?= ../..
VPATH = $(SRCDIR)/apps/vale-ctl

NO_MAN=
CFLAGS = -O2 -pipe
CFLAGS += -Werror -Wall -Wunused-function
CFLAGS += -I $(SRCDIR)/sys -I $(SRCDIR)/apps/include -I $(SRCDIR)/libnetmap
CFLAGS += -Wextra

LDFLAGS += -L $(BUILDDIR)/build-libnetmap
LDLIBS = -lnetmap
PREFIX ?= /usr/local
MAN_PREFIX = $(if $(filter-out /,$(PREFIX)),$(PREFIX),/usr)/share/man

all: $(PROGS)

clean:
	-@rm -rf $(CLEANFILES)

.PHONY: install
install: $(PROGS:%=install-%)

install-%:
	install -D $* $(DESTDIR)/$(PREFIX)/bin/$*
	-install -D -m 644 $(SRCDIR)/apps/vale-ctl/vale-ctl.4 $(DESTDIR)/$(MAN_PREFIX)/man4/vale-ctl.4
