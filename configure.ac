# -*- Autoconf -*-
dnl Process this file with autoconf to produce a configure script.

# Copyright (C) 2013, by Joe Da Silva

AC_PREREQ([2.61])
#-------------------------------------------
# PackageTimestamp version
m4_define([spiro_package_stamp], "20130531")
#-------------------------------------------
# Making point releases:
#   spiro_major_version += 0;
#   spiro_minor_version += 1; (patches or added function(s))
#
# If any new functions have been added:
#   spiro_major_version += 0;
#   spiro_minor_version += 1; (added function(s))
#
# If backwards compatibility has been broken:
#   spiro_major_version += 1;
#   spiro_minor_version = 0;
#
m4_define([spiro_major_version], '0')
m4_define([spiro_minor_version], '1')
m4_define([spiro_version],
          [spiro_major_version.spiro_minor_version.spiro_package_stamp])
m4_define([spiro_info],
          [spiro_major_version:spiro_minor_version:0])
m4_define([spiro_package_name], ["libspiro"])

#-------------------------------------------
AC_INIT([spiro],[spiro_version],[fontforge-devel@lists.sourceforge.net],
	[spiro_package_name],[https://github.com/fontforge/libspiro])
AC_CONFIG_SRCDIR([spiro.c])
AM_INIT_AUTOMAKE([$spiro_package_name],[$spiro_version])
#-------------------------------------------
AC_CONFIG_MACRO_DIR([m4])
LT_INIT
AC_SUBST(LIBTOOL_DEPS)

AC_PROG_CC
AC_PROG_INSTALL
AC_DISABLE_STATIC
AC_ENABLE_SHARED
AC_PROG_LN_S
AC_PROG_MKDIR_P
AC_PROG_MAKE_SET
AC_PROG_SED
AC_PATH_PROGS([WGET],[wget],[wget])

#-------------------------------------------
# Indicate this is a release build and that
# dependancies for changes between Makefile.am
# and Makefile.in should not be checked. This
# makes compiling faster. If you are working
# on the library, run:
# ./configure --enable-maintainer-mode
# to enable the dependancies
dnl AM_MAINTAINER_MODE([enable])

#-------------------------------------------
# I am going to try enabling silent-rules by
# default, so builders are more likely to see
# warnings. # Use --disable-silent-rules or
# "make V=1" if you need to see the rules.
m4_ifdef([AM_SILENT_RULES],[AM_SILENT_RULES([yes])])

#-------------------------------------------
# Platform specific stuff ($host)
AC_CANONICAL_HOST
#-------------------------------------------
# Pass variables to MAKEFILE.AM
AC_SUBST(HOST,$host)
AC_SUBST(FFSPIRO_VERSION,$spiro_info)
#-------------------------------------------
# Check for and add usable compiler warnings
AC_LANG_PUSH([C])
AC_SUBST([WCFLAGS],[])
AX_CHECK_COMPILE_FLAG([-Wall],[WCFLAGS+=" -Wall"])
AX_CHECK_COMPILE_FLAG([-Wextra],[WCFLAGS+=" -Wextra"])
AX_CHECK_COMPILE_FLAG([-Wcast-align],[WCFLAGS+=" -Wcast-align"])
AX_CHECK_COMPILE_FLAG([-Wbad-function-cast],[WCFLAGS+=" -Wbad-function-cast"])
AX_CHECK_COMPILE_FLAG([-Wc++-compat],[WCFLAGS+=" -Wc++-compat"])
AX_CHECK_COMPILE_FLAG([-Wmissing-prototypes],[WCFLAGS+=" -Wmissing-prototypes"])
AX_CHECK_COMPILE_FLAG([-Wunused],[WCFLAGS+=" -Wunused"])
AC_LANG_POP
#-------------------------------------------
AC_PROG_LIBTOOL

AC_CONFIG_FILES([
Makefile
libspiro.pc
])

AC_OUTPUT
