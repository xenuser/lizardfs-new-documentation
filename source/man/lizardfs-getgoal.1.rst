.. _lizardfs-getgoal.1:

*******************
lizardfs-getgoal(1)
*******************

NAME
====

lizardfs-getgoal, lizardfs-setgoal, lizardfs-rgetgoal, lizardfs-rsetgoal - change or retrieve goal

SYNOPSIS
========

::

  lizardfs getgoal [-r] [-n|-h|-H] 'OBJECT'...

  lizardfs rgetgoal [-n|-h|-H] 'OBJECT'...

  lizardfs setgoal [-r] [-n|-h|-H] GOAL_NAME 'OBJECT'...

  lizardfs rsetgoal [-n|-h|-H] GOAL_NAME 'OBJECT'...

DESCRIPTION
===========

**getgoal** and **setgoal** operate on an object's 'goal' value.

getgoal prints current 'goal' value of given object(s). These tools can be used on any file, directory or deleted ('trash') file.

OPTIONS
=======

-r
This option enables recursive mode, which works as usual for every given file,
but for every given directory additionally prints current value of all
contained objects (files and directories).

-n, -h, -H
  These options are described in lizardfs(1).

NOTE
====

**rgetgoal** and **rsetgoal** are deprecated aliases for *getgoal -r* and
*setgoal -r* respectively.

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

lizardfs(1)
