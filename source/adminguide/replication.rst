Configuring Replication Modes
*****************************

LizardFS supports 3 different modes of replication.

In the simplest one, the simple goal setup, you specify how many copies of
every chunk of a file or directory will be copied to how many and optionaly
also "which" chunkservers.
Note that the write modus here is: client writes chunk to ONE chunkserver and
this chunkserver replicates this chunk to the other chunkservers.

The second replication mode is called XOR.


The third and most advanced mode of replication is the EC mode which does
advanced erasure coding with a configurable amount of data and parity copies.
In this mode ....

Now that you know what they are, lets start configuring them....

Setting Goals
=============
Goals configuration is defined in the file mfsgoals.cfg used by the master
server.

Syntax of the mfsgoals.cfg file is::

   	id name : label ...

The # character starts comments.

There can be up to 20 replication goals configured, with ids between 1 and 20
inclusive. Each file stored on the filesystem refers to some goal id and is
replicated according to the goal currently associated with this id.

By default, goal 1 means one copy on any chunkserver, goal 2 means two copies
on any two chunkservers and so on. The purpose of mfsgoals.cfg is to override
this behavior, when desired. The file is a list of goal definitions, each
consisting of an id, a name and a list of labels.

**Id**
  indicates the goal id to be redefined. If some files are already assigned
  this goal id, their effective goal will change.

**Name**
  is a human readable name used by the user interface tools (mfssetgoal,
  mfsgetgoal). A name can consist of up to 32 alphanumeric characters: a-z,
  A-Z, 0-9, _.

**list of labels**
  is a list of chunkserver labels as defined in the mfschunkserver.cfg file.
  A label can consist of up to 32 alphanumeric characters: a-z, A-Z, 0-9, _.
  For each file using this goal and for each label, the system will try to
  maintain a copy of the file on some chunkserver with this label. One label
  may occur multiple times - in such case the system will create one copy per
  each occurence. The special label _ means "a copy on any chunkserver".

Note that changing the definition of a goal in mfsgoals.cfg affects all files
which currently use a given goal id.

Examples
--------

Example of goal definitions::

   	3 3 : _ _ _ # one of the default goals (three copies anywhere)
   	8 not_important_file : _ # only one copy
   	11 important_file : _ _
   	12 local_copy_on_mars : mars _ # at least one copy in the Martian datacenter
   	13 cached_on_ssd : ssd _
   	14 very_important_file : _ _ _ _

For further information see::

  $ man mfsgoals.cfg

Show current goal configuration
-------------------------------

From the command line::

   $ lizardfs-admin list-goals <master ip> <master port>

Via cgi (webinterface):

In the ‘Config’ tab there is a table called ‘Goal definitions’.

Set and show goal of the file/directory
---------------------------------------

**set**

   The goal of a file/direcotry can be set using::

	   $ mfssetgoal goal_name object

   which will result in setting the goal of an object to goal_name.

   By default all new files created in the directory are created with the
   goal of the directory.

   Additional options are:

   * (-r) - change goals recursively for all objects contained in a directory
   * goal_name[+|-] - when goal_name is appended with +, the goal is changed
   only if it will “increase security” (i.e. goal_name id is higher than id
   of the current goal)


**show**

   Current goal of the file/directory can be shown using::

      $ mfsgetgoal object

   Result is the name of the currently set goal.

   To list the goals in a directory use::

      $ mfsgetgoal -r directory

   which for every given directory additionally prints the current value of
   all contained objects (files and directories).

   To show where exactly file chunks are located use::

      $ mfsfileinfo file

For further information see: man mfssetgoal, man mfsfileinfo



Setting up XOR
==============


Setting up EC
==============