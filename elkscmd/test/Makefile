.PHONY: all clean

SUBDIRS =  \
	eth    \
	fat    \
	pty    \
	socket \
	select \
	signal \
	# EOL

.PHONY: $(SUBDIRS)

all: $(SUBDIRS)
	@for DIR in $(SUBDIRS); do $(MAKE) -C $$DIR all || exit 1; done

install: $(SUBDIRS)
	@for DIR in $(SUBDIRS); do $(MAKE) -C $$DIR install || exit 1; done

clean: $(SUBDIRS)
	@for DIR in $(SUBDIRS); do $(MAKE) -C $$DIR clean || exit 1; done
