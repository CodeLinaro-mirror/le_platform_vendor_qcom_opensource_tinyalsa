pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = tinyalsa.pc
EXTRA_DIST = $(pkgconfig_DATA)

AM_CFLAGS = -Wundef \
        -Wstrict-prototypes \
        -Wno-trigraphs \
        -g -O0 \
        -fno-inline \
        -fno-short-enums \
        -fpic \
        -fstack-protector-all

if BUILDSYSTEM_OPENWRT

AM_CFLAGS += -I ./include

h_sources = ./include/tinyalsa/asoundlib.h \
            ./include/tinyalsa/mixer_plugin.h \
            ./include/tinyalsa/pcm_plugin.h

c_sources = ./mixer.c \
            ./pcm.c \
            ./mixer_hw.c \
            ./mixer_plugin.c \
            ./pcm_hw.c \
            ./pcm_plugin.c \
            ./snd_utils.c

else

AM_CFLAGS += -I $(top_srcdir)/include

h_sources = ${top_srcdir}/include/tinyalsa/asoundlib.h \
            ${top_srcdir}/include/tinyalsa/mixer_plugin.h \
            ${top_srcdir}/include/tinyalsa/pcm_plugin.h

c_sources = ${top_srcdir}/mixer.c \
            ${top_srcdir}/pcm.c \
            ${top_srcdir}/mixer_hw.c \
            ${top_srcdir}/mixer_plugin.c \
            ${top_srcdir}/pcm_hw.c \
            ${top_srcdir}/pcm_plugin.c \
            ${top_srcdir}/snd_utils.c
endif


library_includedir = $(includedir)/tinyalsa/
library_include_HEADERS = $(h_sources)

lib_LTLIBRARIES = libtinyalsa.la
libtinyalsa_la_SOURCES = $(c_sources)
libtinyalsa_la_LIBADD = $(GLIB_LIBS)
libtinyalsa_la_CFLAGS := $(AM_CFLAGS)
libtinyalsa_la_CFLAGS += $(GLIB_CFLAGS) -Dstrlcpy=g_strlcpy -Dstrlcat=g_strlcat -include glib.h
libtinyalsa_la_CFLAGS += -D__unused=__attribute__\(\(__unused__\)\)
libtinyalsa_la_CFLAGS += -DNDEBUG
libtinyalsa_la_LDFLAGS = -shared -avoid-version

bin_PROGRAMS = qtitinyplay

qtitinyplay_SOURCES := ./tinyplay.c
qtitinyplay_la_LIBADD = $(GLIB_LIBS)
qtitinyplay_la_CFLAGS := $(GLIB_CFLAGS) -Dstrlcpy=g_strlcpy -Dstrlcat=g_strlcat -include glib.h
qtitinyplay_la_CFLAGS += -D__unused=__attribute__\(\(__unused__\)\)
qtitinyplay_LDADD = libtinyalsa.la $(GLIB_LIBS) -ldl
qtitinyplay_la_LDFLAGS = -shared -avoid-version

bin_PROGRAMS += qtitinycap

qtitinycap_SOURCES := ./tinycap.c
qtitinycap_la_LIBADD = $(GLIB_LIBS)
qtitinycap_CFLAGS := $(AM_CFLAGS) $(GLIB_CFLAGS) -Dstrlcpy=g_strlcpy -Dstrlcat=g_strlcat -include glib.h
qtitinycap_CFLAGS += -D__unused=__attribute__\(\(__unused__\)\)
qtitinycap_LDADD = libtinyalsa.la $(GLIB_LIBS) -ldl
qtitinycap_la_LDFLAGS = -shared -avoid-version

bin_PROGRAMS += qtitinymix

qtitinymix_SOURCES := ./tinymix.c
qtitinymix_la_LIBADD = $(GLIB_LIBS)
qtitinymix_la_CFLAGS := $(GLIB_CFLAGS) -Dstrlcpy=g_strlcpy -Dstrlcat=g_strlcat -include glib.h
qtitinymix_la_CFLAGS += -D__unused=__attribute__\(\(__unused__\)\)
qtitinymix_LDADD = libtinyalsa.la $(GLIB_LIBS) -ldl
qtitinymix_la_LDFLAGS = -shared -avoid-version

bin_PROGRAMS += tinymix

tinymix_SOURCES := ./tinymix.c
tinymix_la_LIBADD = $(GLIB_LIBS)
tinymix_la_CFLAGS := $(GLIB_CFLAGS) -Dstrlcpy=g_strlcpy -Dstrlcat=g_strlcat -include glib.h
tinymix_la_CFLAGS += -D__unused=__attribute__\(\(__unused__\)\)
tinymix_LDADD = libtinyalsa.la $(GLIB_LIBS) -ldl
tinymix_la_LDFLAGS = -shared -avoid-version

bin_PROGRAMS += qtitinyhostless

qtitinyhostless_SOURCES := ./tinyhostless.c
qtitinyhostless_la_LIBADD = $(GLIB_LIBS)
qtitinyhostless_la_CFLAGS := $(GLIB_CFLAGS) -Dstrlcpy=g_strlcpy -Dstrlcat=g_strlcat -include glib.h
qtitinyhostless_la_CFLAGS += -D__unused=__attribute__\(\(__unused__\)\)
qtitinyhostless_LDADD = libtinyalsa.la $(GLIB_LIBS) -ldl
qtitinyhostless_la_LDFLAGS = -shared -avoid-version

bin_PROGRAMS += qtitinypcminfo

qtitinypcminfo_SOURCES := ./tinypcminfo.c
qtitinypcminfo_la_LIBADD = $(GLIB_LIBS)
qtitinypcminfo_la_CFLAGS := $(GLIB_CFLAGS) -Dstrlcpy=g_strlcpy -Dstrlcat=g_strlcat -include glib.h
qtitinypcminfo_la_CFLAGS += -D__unused=__attribute__\(\(__unused__\)\)
qtitinypcminfo_LDADD = libtinyalsa.la $(GLIB_LIBS) -ldl
qtitinypcminfo_la_LDFLAGS = -shared -avoid-version
