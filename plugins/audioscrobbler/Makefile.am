plugindir = $(PLUGINDIR)
plugindatadir = $(PLUGIN_DATA_DIR)
plugin_LTLIBRARIES = libaudioscrobbler.la

libaudioscrobbler_la_SOURCES = \
	ario-audioscrobbler-plugin.c \
	ario-audioscrobbler.c \
        ario-audioscrobbler.h

libaudioscrobbler_la_LDFLAGS = $(PLUGIN_LIBTOOL_FLAGS)

libaudioscrobbler_la_LIBADD =  $(SOUP_LIBS)

INCLUDES = 						\
	-DLOCALE_DIR=\""$(prefix)/$(DATADIRNAME)/locale"\"	\
	$(DEPS_CFLAGS)   				\
	$(SOUP_CFLAGS)   				\
	-I$(top_srcdir) 				\
	-I$(top_srcdir)/src      			\
	-I$(top_srcdir)/src/lib                        	\
	-I$(top_srcdir)/src/plugins                   	\
	-I$(top_srcdir)/src/shell                       \
	$(WARNINGS)

uidir = $(plugindatadir)
ui_DATA = audioscrobbler-prefs.ui

plugin_in_files = audioscrobbler.ario-plugin.desktop.in

%.ario-plugin: %.ario-plugin.desktop.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*po) ; $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache

plugin_DATA = $(plugin_in_files:.ario-plugin.desktop.in=.ario-plugin)

icondir = $(plugindatadir)/icons
icon_DATA = audioscrobbler.png

EXTRA_DIST = $(plugin_in_files)         \
             $(plugin_DATA)             \
             $(icon_DATA)               \
	     $(ui_DATA)

CLEANFILES = $(plugin_DATA)
DISTCLEANFILES = $(plugin_DATA)
