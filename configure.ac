# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.68])
AC_INIT([libmd], [m4_esyscmd([./get-version])], [libbsd@lists.freedesktop.org])
AC_CONFIG_SRCDIR([src/sha2.c])
AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_MACRO_DIR([m4])

AM_INIT_AUTOMAKE([1.8 -Wall foreign nostdinc no-dist-gzip dist-xz])

m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])],
                            [AC_SUBST([AM_DEFAULT_VERBOSITY], [1])])

LIBMD_ABI_MAJOR=0
LIBMD_ABI_MINOR=0
LIBMD_ABI_PATCH=4

LIBMD_ABI="$LIBMD_ABI_MAJOR:$LIBMD_ABI_MINOR:$LIBMD_ABI_PATCH"
AC_SUBST([LIBMD_ABI])

# Checks for operating system services and capabilities.
AC_USE_SYSTEM_EXTENSIONS
AC_SYS_LARGEFILE

AM_PROG_AR
LT_INIT
LIBMD_LINKER_VERSION_SCRIPT

# Checks for programs.
AC_PROG_CC

# Checks for libraries.

# Checks for header files.
AC_CHECK_HEADERS([unistd.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_C_BIGENDIAN
AC_TYPE_OFF_T
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T

# Checks for library functions.

AC_CONFIG_FILES([
	Makefile
	include/Makefile
	man/Makefile
	src/Makefile
	src/libmd.pc
	test/Makefile
])
AC_CONFIG_HEADERS([config.h])
AC_OUTPUT
