AC_INIT([wmfire], [1.2.4])
AC_CONFIG_SRCDIR([src/wmfire.c])
AM_INIT_AUTOMAKE

AC_PROG_AWK
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_LN_S

AC_PATH_X
AC_CHECK_LIB(X11, main)
AC_CHECK_LIB(Xext, main)
AC_CHECK_LIB(m,sincos)

AC_HEADER_DIRENT
AC_HEADER_STDC
AC_HEADER_SYS_WAIT
AC_CHECK_HEADERS(unistd.h)

AC_C_CONST

AC_ARG_ENABLE(header, [
Wmfire options:
])

AC_ARG_ENABLE(session,
[  --enable-session                Compile with session management],
       session=on, session=off)

if test "x$session" = "xon" ; then
  AC_DEFINE(SESSION)
  LDFLAGS="$LDFLAGS -lSM -lICE"
fi
AM_CONDITIONAL(SESSION, test "x$session" = "xon")

PKG_CHECK_MODULES([GTK2],[gtk+-2.0],[
  GTK2_LIBS=`echo "$GTK2_LIBS" | sed -e "s/-lgtk-x11-2.0//g" -e "s/-latk-1.0//g"`
])

PKG_CHECK_MODULES([GTOP],[libgtop-2.0])

CFLAGS="$CFLAGS $GTK2_CFLAGS $GTOP_CFLAGS"
LDFLAGS="$LDFLAGS $GTK2_LIBS $GTOP_LIBS"

AC_CHECK_FUNCS(strstr)

AC_OUTPUT(Makefile src/Makefile)
