#**************************************************************************
#*                                                                        *
#*                                 OCaml                                  *
#*                                                                        *
#*            Xavier Leroy, projet Cristal, INRIA Rocquencourt            *
#*                                                                        *
#*   Copyright 1999 Institut National de Recherche en Informatique et     *
#*     en Automatique.                                                    *
#*                                                                        *
#*   All rights reserved.  This file is distributed under the terms of    *
#*   the GNU Lesser General Public License version 2.1, with the          *
#*   special exception on linking described in the file LICENSE.          *
#*                                                                        *
#**************************************************************************

# Makefile for the Unix interface library

LIBNAME=unix

EXTRACAMLFLAGS=-nolabels

# dllunix.so particularly requires libm for modf symbols
LDOPTS=$(NATIVECCLIBS)

COBJS=accept.o access.o addrofstr.o alarm.o bind.o channels.o chdir.o \
  chmod.o chown.o chroot.o close.o fsync.o closedir.o connect.o cst2constr.o \
  cstringv.o dup.o dup2.o envir.o errmsg.o execv.o execve.o execvp.o exit.o \
  fchmod.o fchown.o fcntl.o fork.o ftruncate.o \
  getaddrinfo.o getcwd.o getegid.o geteuid.o getgid.o \
  getgr.o getgroups.o gethost.o gethostname.o getlogin.o \
  getnameinfo.o getpeername.o getpid.o getppid.o getproto.o getpw.o \
  gettimeofday.o getserv.o getsockname.o getuid.o gmtime.o \
  initgroups.o isatty.o itimer.o kill.o link.o listen.o lockf.o lseek.o \
  mkdir.o mkfifo.o mmap.o mmap_ba.o \
  nice.o open.o opendir.o pipe.o putenv.o read.o \
  readdir.o readlink.o rename.o rewinddir.o rmdir.o select.o sendrecv.o \
  setgid.o setgroups.o setsid.o setuid.o shutdown.o signals.o \
  sleep.o socket.o socketaddr.o \
  socketpair.o sockopt.o stat.o strofaddr.o symlink.o termios.o \
  time.o times.o truncate.o umask.o unixsupport.o unlink.o \
  utimes.o wait.o write.o

CAMLOBJS=unix.cmo unixLabels.cmo

HEADERS=unixsupport.h socketaddr.h

include ../Makefile

.PHONY: depend
depend:
ifeq "$(TOOLCHAIN)" "msvc"
	$(error Dependencies cannot be regenerated using the MSVC ports)
else
	$(CC) -MM $(OC_CPPFLAGS) *.c > .depend
	$(CAMLRUN) ../../tools/ocamldep -slash *.mli *.ml >> .depend
endif

include .depend
