# Copyright (c) Facebook, Inc. and its affiliates.

# This source code is licensed under the MIT license found in the
# LICENSE file in the root directory of this source tree.

AC_INIT(liblogfaf, [1.0], [antont@fb.com])
AC_CONFIG_SRCDIR([src/liblogfaf.c])
AM_CONFIG_HEADER([config.h])
AM_INIT_AUTOMAKE([foreign])

AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_LN_S

AC_ENABLE_SHARED
AC_DISABLE_STATIC
AC_PROG_LIBTOOL

AC_HEADER_STDC
AC_C_CONST

AC_MSG_CHECKING([build with debug output])
AC_ARG_ENABLE([debug],
              [AS_HELP_STRING([--enable-debug],
                              [enable debug output [default=no]])],
                              [debug_enabled="$enableval"],
                              [debug_enabled=no])
AC_MSG_RESULT([$debug_enabled])

if test x"$debug_enabled" != x"yes"; then
    AM_CFLAGS="$AM_CFLAGS -DNDEBUG"
fi

SYSTEM=`uname -s 2>/dev/null`
case "$SYSTEM" in
	"Linux"|"Darwin")
		DL_LDLIBS="-ldl"
		;;
	"FreeBSD")
		DL_LDLIBS="-lc"
		;;
	*)
		AC_MSG_ERROR(["Unsupported platform: $SYSTEM"])
		;;
esac

AC_SUBST([AM_CFLAGS])
AC_SUBST([DL_LDLIBS])

AC_CONFIG_FILES([Makefile src/Makefile])
AC_OUTPUT
