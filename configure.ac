#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([rtbxegen], [0.1], [nguy0066@e.ntu.edu.sg])

AC_CONFIG_SRCDIR([src/exchanges/rtbxegen_exchange_runner.cpp],[examples/hello_world.cpp])
AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_HEADERS([config.h])

AM_INIT_AUTOMAKE([1.11 foreign dist-bzip2 nostdinc subdir-objects])

# use the C++ compiler for the following checks
AC_LANG([C++])

# Checks for header files.
AC_HEADER_STDC
AC_CHECK_HEADERS([string])
AC_CHECK_HEADERS([iostream])

# Checks for programs.
AC_PROG_CC
AC_PROG_CXX
AC_PROG_CXXCPP

AC_PROG_INSTALL
AM_PROG_LIBTOOL

# initialize libtool
LT_INIT

# build with c++11 flag
AC_SUBST([AM_CXXFLAGS], [-std=c++11])

# TODO: this should be remove but for now; proxygen doesn't install some certain header files to standard header folder
# which cause error when build
# GLOBAL_INCLUDE_DIR="-I/home/vagrant/data/proxygen -I$(top_srcdir)"
AC_SUBST([AM_CPPFLAGS], ["-I/home/vagrant/data/proxygen -I/home/vagrant/data/rtbxegen"])

# Checks for libraries.
# AC_CHECK_LIB([proxygenhttpserver], [folly], [glog], [gflags], [pthread])

# Checks for header files.

# Checks for typedefs, structures, and compiler characteristics.

# Checks for library functions.
# Checks for glog and gflags
# There are no symbols with C linkage, so we do a try-run
AC_HAVE_LIBRARY([glog],[],[AC_MSG_ERROR(
                [Please install google-glog library])])
AC_HAVE_LIBRARY([gflags],[],[AC_MSG_ERROR(
                [Please install google-gflags library])])

PKG_CHECK_MODULES([protobuf], [protobuf])

AC_CONFIG_FILES([
 Makefile
 lib/Makefile
 lib/common/Makefile
 lib/proxygen/Makefile
 lib/openrtb/Makefile
 lib/openrtb/tests/Makefile
 tests/Makefile
 src/Makefile
 src/exchanges/Makefile
 examples/Makefile
 examples/tests/Makefile
])

##########################################################################
# debug compilation support
##########################################################################

AC_MSG_CHECKING([whether to build with debug information])
AC_ARG_ENABLE([debug],
    [AS_HELP_STRING([--enable-debug],
        [enable debug data generation (def=no)])],
    [debugit="$enableval"],
    [debugit=no])
AC_MSG_RESULT([$debugit])

if test x"$debugit" = x"yes"; then
    AC_DEFINE([DEBUG],[],[Debug Mode])
    AM_CXXFLAGS="$AM_CXXFLAGS -g -Wall -Werror -Wno-uninitialized -O0"
else
    AC_DEFINE([NDEBUG],[],[No-debug Mode])
    AM_CXXFLAGS="$AM_CXXFLAGS -O3"
fi

##########################################################################


AC_OUTPUT
