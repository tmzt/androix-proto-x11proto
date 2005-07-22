AC_PREREQ([2.57])
AC_INIT([Xproto], [7.0], [xorg@lists.freedesktop.org])
AM_INIT_AUTOMAKE([foreign dist-bzip2])

fds_bits_found=false;

if test "x$fds_bits_found" = xfalse ; then
   AC_CHECK_MEMBER(fd_set.fds_bits, 
			   [
			       fds_bits_found=plain
			       USE_FDS_BITS="fds_bits"
			   ],,
			   [
			       #include <sys/select.h>
			   ])
fi

if test "x$fds_bits_found" = xfalse ; then
   AC_CHECK_MEMBER(fd_set.__fds_bits,
			[
			    fds_bits_found=underscores
			    USE_FDS_BITS="__fds_bits"
			],,
			[
			    #include <sys/select.h>
			])
fi

if test "x$fds_bits_found" = xfalse ; then
    AC_MSG_ERROR([Could not determine how to access the fds_bits or equivalent
                  structure in fd_set on your platform.])
fi

AC_SUBST([USE_FDS_BITS])
 
AC_OUTPUT([Makefile
           Xpoll.h
           xproto.pc])
