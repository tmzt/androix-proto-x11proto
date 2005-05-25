AC_PREREQ([2.57])
AC_INIT([Xproto], [7.0], [xorg@lists.freedesktop.org])
AM_INIT_AUTOMAKE([foreign dist-bzip2])
#
PROTO_DEFINES=


# Find out what defines are necessary to make struct fd_set contain
# fds_bits
# 

fds_bits_found=false;

# No defines necessary?
if test x$fds_bits_found = xfalse ; then
   AC_CHECK_MEMBER(fd_set.fds_bits, 
			   [
			       fds_bits_found=true
			   ],,
			   [
			       #include <sys/select.h>
			   ])
fi

# With _XOPEN_SOURCE?

unset ac_cv_member_fd_set_fds_bits

if test x$fds_bits_found = xfalse ; then
   AC_CHECK_MEMBER(fd_set.fds_bits, 
			[
			    fds_bits_found=true
			    PROTO_DEFINES="$PROTO_DEFINES -D_XOPEN_SOURCE"
			],,
			[
			    #define _XOPEN_SOURCE
			    #include <sys/select.h>
			])
fi

AC_SUBST(PROTO_DEFINES)
 
AC_OUTPUT([Makefile
           xproto.pc])
