#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.63])
dnl AC_INIT([nscmp], [1.0])
AC_INIT([NSCMP C++ Package],
        [1.0.0],
        [cplusplus@novasparks.com],
        [nscmp])
AC_CANONICAL_SYSTEM
AM_INIT_AUTOMAKE([-Wall -Werror -Wno-portability foreign])
LT_PREREQ([2.2])
AC_CONFIG_SRCDIR([config_placeholder.h.in])
AC_CONFIG_HEADER(config_placeholder.h)
AC_CONFIG_MACRO_DIR([m4])
AC_COPYRIGHT([NovaSparks Confidential
              (c) Copyright NovaSparks. 2010, 2016
              The source code for this program is not published or otherwise
              divested of its trade secrets.])

# Checks for programs.
AC_PROG_CXX
AC_PROG_AWK
AC_PROG_CC
AC_PROG_CPP
AC_PROG_INSTALL
AC_PROG_LN_S
AC_PROG_MAKE_SET
AC_PROG_MKDIR_P
AC_OPENMP
AC_LANG(C++)

m4_ifdef([AM_PROG_AR], [AM_PROG_AR])

LT_INIT([dlopen])


NSCMP_CFLAGS=
NSCMP_LDFLAGS=
dnl nspcie setting options for dev
AM_NSPCIE_OPTS
AC_SUBST(NSPCIE_VERSION, [$am_nspcie_version])
AC_SUBST(NSPCIE_RELEASE, [$am_nspcie_release])
AC_SUBST(NSPCIE_DIR, [$am_nspcie_dir])
AC_SUBST(NSPCIE_LIBDIRS, [$am_nspcie_libdirs])
AC_SUBST(NSPCIE_LIBEXECDIRS, [$am_nspcie_libexecdirs])
AC_SUBST(NSPCIE_INCLUDEDIRS, [$am_nspcie_includedirs])
for d in $NSPCIE_INCLUDEDIRS; do NSCMP_CFLAGS+=" -I$d"; done
for d in $NSPCIE_LIBDIRS; do NSCMP_LDFLAGS+=" -L$d"; done

dnl nsmsg setting options for dev
AM_NSMSG_OPTS
AC_SUBST(NSMSG_VERSION, [$am_nsmsg_version])
AC_SUBST(NSMSG_RELEASE, [$am_nsmsg_release])
AC_SUBST(NSMSG_DIR, [$am_nsmsg_dir])
AC_SUBST(NSMSG_LIBDIRS, [$am_nsmsg_libdirs])
AC_SUBST(NSMSG_LIBEXECDIRS, [$am_nsmsg_libexecdirs])
AC_SUBST(NSMSG_INCLUDEDIRS, [$am_nsmsg_includedirs])
for d in $NSMSG_INCLUDEDIRS; do NSCMP_CFLAGS+=" -I$d"; done
for d in $NSMSG_LIBDIRS; do NSCMP_LDFLAGS+=" -L$d"; done

dnl nsbdl setting options for dev
AM_NSBDL_OPTS
AC_SUBST(NSBDL_VERSION, [$am_nsbdl_version])
AC_SUBST(NSBDL_RELEASE, [$am_nsbdl_release])
AC_SUBST(NSBDL_DIR, [$am_nsbdl_dir])
AC_SUBST(NSBDL_LIBDIRS, [$am_nsbdl_libdirs])
AC_SUBST(NSBDL_LIBEXECDIRS, [$am_nsbdl_libexecdirs])
AC_SUBST(NSBDL_INCLUDEDIRS, [$am_nsbdl_includedirs])
for d in $NSBDL_INCLUDEDIRS; do NSCMP_CFLAGS+=" -I$d"; done
for d in $NSBDL_LIBDIRS; do NSCMP_LDFLAGS+=" -L$d"; done

dnl nsdec setting options for dev
AM_NSDEC_OPTS
AC_SUBST(NSDEC_VERSION, [$am_nsdec_version])
AC_SUBST(NSDEC_RELEASE, [$am_nsdec_release])
AC_SUBST(NSDEC_DIR, [$am_nsdec_dir])
AC_SUBST(NSDEC_LIBDIRS, [$am_nsdec_libdirs])
AC_SUBST(NSDEC_LIBEXECDIRS, [$am_nsdec_libexecdirs])
AC_SUBST(NSDEC_INCLUDEDIRS, [$am_nsdec_includedirs])
AC_SUBST(NSDEC_NSWF_VER, [$am_nsdec_nswf_ver])
AC_SUBST(NSDEC_NSWF_VERSION, [$am_nsdec_nswf_version])
AC_SUBST(NSDEC_NSWF_NUM, [$am_nsdec_nswf_num])
AC_SUBST(NSDEC_NSWF_DATE, [$am_nsdec_nswf_date])
for d in $NSDEC_INCLUDEDIRS; do NSCMP_CFLAGS+=" -I$d"; done
for d in $NSDEC_LIBDIRS; do NSCMP_LDFLAGS+=" -L$d"; done

CXXFLAGS=$NSCMP_CFLAGS
LDFLAGS=$NSCMP_LDFLAGS

dnl NSBL Macros
AC_NSBDL([], [], [AC_MSG_ERROR([Cannot configure nsbdl core])], [1])
AC_NSBDL_CPPUNIT
AC_NSBDL_NSMSG
AC_NSBDL_NSPCIE

# Checks for programs.
AC_PROG_CXX
AC_PROG_AWK
AC_PROG_CC
AC_PROG_CPP
AC_PROG_INSTALL
AC_PROG_LN_S
AC_PROG_MAKE_SET
AC_PROG_LN_S

dnl Check for an existing doxygen source documentation program
dnl It sets or uses the environment variable DOXYGEN
AC_CHECK_PROGS([DOXYGEN], [doxygen])

# Create Automake conditional based on the DOXYGEN variable
AM_CONDITIONAL([HAVE_DOXYGEN], [test -n "$DOXYGEN"])
AM_COND_IF([HAVE_DOXYGEN], [AC_CONFIG_FILES([doc/doxygen/nscmp.conf doc/doxygen/nscmp.dox])])
#AS_IF([test -n "$DOXYGEN"], [AC_CONFIG_FILES([docs/doxyfile])])

# Check CPPLINT
AC_PATH_PROG([CPPLINT], [cpplint.py], [true])
AS_IF([test "x$CPPLINT" = xtrue],
          [AC_MSG_WARN([We recommend cpplint.py for developing this package.
           Get it from https://google-styleguide.googlecode.com/svn/trunk/cpplint/cpplint.py
           and put it in your path, or point the CPPLINT environment variable at it.])])

#Common configure options.
AC_ARG_ENABLE(debug, AS_HELP_STRING([--enable-debug],[Turn on debug]), [debug="$enableval"], [debug="no"])

AC_MSG_CHECKING([NSCMP_REVISION])
AC_ARG_VAR(NSCMP_REVISION, [NSCMP svn revision])

AC_MSG_CHECKING([NSCMP_PRODUCT])
AC_ARG_VAR(NSCMP_PRODUCT, [NSCMP Product Name])

CPPLINTOPTS=--filter=-build/header_guard,-whitespace/comments,-readability/streams,-runtime/reference,-build/c++11

PRODUCT_NAME=${NSCMP_PRODUCT:-"_trunk"}
dnl Get svn revision and update revision file
if test -n "$NSCMP_REVISION"; then
  SVN_REVISION=$NSCMP_REVISION;
else
  SVN_REVISION=`cd ${srcdir} && svn info | grep 'Last Changed Rev' | cut -d' ' -f4 && cd - &>/dev/null`
fi

AC_MSG_NOTICE([SVN_REVISION: $SVN_REVISION])
AC_MSG_NOTICE([PRODUCT_NAME: $PRODUCT_NAME])

NSCMP_RELEASE="$SVN_REVISION$PRODUCT_NAME"

if test "x$debug" = "xyes" ;then
    AM_CONDITIONAL(DEBUG,true)
    AC_DEFINE(DEBUG,[1],["Debug the code"])
else
    AM_CONDITIONAL(DEBUG,false)
    AC_DEFINE(DEBUG,[0],["Do not debug"])
fi

if test -z "$OPENMP_CFLAGS" ;then
    CFLAGS+=" -pthread" #enables pthreads feature and links in the library
else
    CFLAGS+=" $OPENMP_CFLAGS"
fi

# Checks for libraries.
dnl AC_NSBDL_CHECK_LIB(nsfc,,[AC_MSG_ERROR([Cannot find libnsfc of nsbdl package])])
dnl AC_NSBDL_CHECK_LIB(net,,[AC_MSG_ERROR([Cannot find libnet of nsbdl package])])
dnl AC_NSBDL_CHECK_LIB(capture,,[AC_MSG_ERROR([Cannot find libcapture of nsbdl package])])
dnl AC_NSBDL_CHECK_LIB(settings,,[AC_MSG_ERROR([Cannot find libsettings of nsbdl package])])
dnl AC_NSBDL_CHECK_LIB(nsjson,,[AC_MSG_ERROR([Cannot find nsjson of nsbdl package])])

# Checks for header files.
AC_CHECK_HEADERS([limits.h])
AC_CHECK_HEADERS([sys/param.h])
dnl check nsfc headers
AC_CHECK_HEADERS(nsfc/nsfc.h,,[AC_MSG_ERROR([Cannot find file nsfc/nsfc.h of nsbdl package, install nsbdl package])])

# Checks for typedefs, structures, and compiler characteristics.
AC_HEADER_STDBOOL
AC_C_INLINE
AC_TYPE_INT16_T
AC_TYPE_INT32_T
AC_TYPE_INT64_T
AC_TYPE_INT8_T
AC_TYPE_OFF_T
AC_TYPE_PID_T
AC_C_RESTRICT
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T
AC_TYPE_UINT16_T
AC_TYPE_UINT32_T
AC_TYPE_UINT64_T
AC_TYPE_UINT8_T
AC_CHECK_TYPES([ptrdiff_t])

# Checks for library functions.
AC_FUNC_MMAP
AC_FUNC_REALLOC
AC_FUNC_STRERROR_R
AC_FUNC_ERROR_AT_LINE
AC_CHECK_FUNCS([strtol strtoull])


AC_SUBST(CPPLINTOPTS)
AC_SUBST(SVN_REVISION)
AC_SUBST(PRODUCT_NAME)
AC_SUBST(NSCMP_RELEASE)
AC_SUBST(debug)

LIBS="-lsettings -lnsjson -lcapture -lnet -lnsfc $LIBS"

AC_CONFIG_FILES([Makefile
                 include/Makefile
                 lib/Makefile
                 package/Makefile
                 package/nscmp.spec
                 m4-nscmp-devel/Makefile
                 src/Makefile
                 src/exchange/Makefile
                 src/data/Makefile
                 src/comparator/common/Makefile
                 src/comparator/novasparks/nswf/Makefile
                 src/comparator/novasparks/lq2/Makefile
                 src/consumer/common/Makefile
                 src/consumer/novasparks/nswf/Makefile
                 src/consumer/novasparks/lq2/Makefile
                 doc/Makefile
                 doc/doxygen/Makefile
                 common.gmake])
AC_OUTPUT

echo "
NSCMP toolkit ($PACKAGE_NAME) version $PACKAGE_VERSION
Prefix.........: $prefix
Debug Build....: $debug
C++ Compiler...: $CXX $CXXFLAGS $CPPFLAGS
Linker.........: $LIBS $EXTRALIBS
Doxygen........: ${DOXYGEN:-NONE}
"
