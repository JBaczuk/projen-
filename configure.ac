#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([projenpp], [0.1.0], [https://github.com/JBaczuk/projenpp/issues])
AM_INIT_AUTOMAKE(subdir-objects)
AC_CONFIG_SRCDIR([src/main.cpp])
AC_CONFIG_HEADERS([config.h])

# Specify the directory of additional local Autoconf macros.
AC_CONFIG_MACRO_DIR([m4])

# Checks for programs.
AC_PROG_CXX

# Check for baseline language coverage in the compiler for the C++11 standard.
#------------------------------------------------------------------------------
AX_CXX_COMPILE_STDCXX_11([noext], [mandatory])

# Require c++11 for all c++ products.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-std=c++11],
[CXXFLAGS="$CXXFLAGS -std=c++11"])])

# Check for pkg-config.
PKG_PROG_PKG_CONFIG
AS_IF([test -n "$PKG_CONFIG"],,
    [AC_MSG_ERROR([pkg-config is required but was not found.])])

# Curl
AX_PATH_GENERIC(curl,7.58.0,,,
    [AC_MSG_ERROR([libcurl is required but was not found.])])

# Boost
# ---------------------
AX_BOOST_BASE([1.47.0],,
    [AC_MSG_ERROR([boost >= 1.47.0 required but not found])])

AX_BOOST_SYSTEM
AX_BOOST_PROGRAM_OPTIONS
AX_BOOST_UNIT_TEST_FRAMEWORK

# Checks for header files.

# Checks for typedefs, structures, and compiler characteristics.

# Checks for library functions.

AC_CONFIG_FILES([Makefile
                 src/Makefile
                 test/Makefile])
AC_OUTPUT
