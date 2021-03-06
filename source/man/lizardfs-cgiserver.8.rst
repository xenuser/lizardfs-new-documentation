.. _lizardfs-cgiserver.8:

*********************
lizardfs-cgiserver(8)
*********************

NAME
====

lizardfs-cgiserver - simple HTTP/CGI server for Lizard File System monitoring

SYNOPSIS
========

::

  lizardfs-cgiserver [-H 'BIND-HOST'] [-P 'BIND-PORT'] [-R 'ROOT-PATH'] [-v]
  lizardfs-cgiserver* -h

DESCRIPTION
===========

**lizardfs-cgiserver** is a very simple HTTP server capable of running CGI
scripts for Lizard File System monitoring. It just runs in foreground and
works until killed with e.g. SIGINT or SIGTERM.

OPTIONS
=======

-h
  print usage information and exit

-H <BIND_HOST>
  local address to listen on (default: any)

-P <BIND_PORT>
  port to listen on (default: 9425)

-R <ROOT_PATH>
  local path to use as HTTP document root (default is CGIDIR set up at
  configure time)

-v
  log requests on stderr

COPYRIGHT
=========


Copyright 2008-2009 Gemius SA, 2013-2016 Skytechnology Sp. z o.o.

LizardFS is free software: you can redistribute it and/or modify it under the
terms of the GNU General Public License as published by the Free Software
Foundation, version 3.

LizardFS is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR
A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with
LizardFS. If not, see <http://www.gnu.org/licenses/>.

SEE ALSO
========

lizardfs(7)
