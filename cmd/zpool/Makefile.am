include $(top_srcdir)/config/Rules.am

DEFAULT_INCLUDES += \
	-I$(top_srcdir)/include \
	-I$(top_srcdir)/lib/libspl/include

sbin_PROGRAMS = zpool

zpool_SOURCES = \
	zpool_iter.c \
	zpool_main.c \
	zpool_util.c \
	zpool_util.h \
	zpool_vdev.c

zpool_LDADD = \
	$(top_builddir)/lib/libnvpair/libnvpair.la \
	$(top_builddir)/lib/libuutil/libuutil.la \
	$(top_builddir)/lib/libzpool/libzpool.la \
	$(top_builddir)/lib/libzfs/libzfs.la \
	$(top_builddir)/lib/libzfs_core/libzfs_core.la \
	-lm $(LIBBLKID)

zpoolconfdir = $(sysconfdir)/zfs/zpool.d
zpoolexecdir = $(libexecdir)/zfs/zpool.d

EXTRA_DIST = zpool.d/README

dist_zpoolexec_SCRIPTS = \
	zpool.d/enc \
	zpool.d/encdev \
	zpool.d/fault_led \
	zpool.d/iostat \
	zpool.d/iostat-1s \
	zpool.d/iostat-10s \
	zpool.d/label \
	zpool.d/locate_led \
	zpool.d/lsblk \
	zpool.d/model \
	zpool.d/serial \
	zpool.d/ses \
	zpool.d/size \
	zpool.d/slaves \
	zpool.d/slot \
	zpool.d/upath \
	zpool.d/vendor

zpoolconfdefaults = \
	enc \
	encdev \
	fault_led \
	iostat \
	iostat-1s \
	iostat-10s \
	label \
	locate_led \
	lsblk \
	model \
	serial \
	ses \
	size \
	slaves \
	slot \
	upath \
	vendor

install-data-hook:
	$(MKDIR_P) "$(DESTDIR)$(zpoolconfdir)"
	for f in $(zpoolconfdefaults); do \
	  test -f "$(DESTDIR)$(zpoolconfdir)/$${f}" -o \
	       -L "$(DESTDIR)$(zpoolconfdir)/$${f}" || \
	    ln -s "$(zpoolexecdir)/$${f}" "$(DESTDIR)$(zpoolconfdir)"; \
	done
