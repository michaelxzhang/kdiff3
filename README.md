# KDiff3
Original copied from 'git clone https://git.code.sf.net/p/kdiff3/code kdiff3-code'

Made changes to followings:
1. Put lines at top and bottom of the current selection range
2. Fill a rectange will pattern if noline

Here's what's looks like:
![kdiff3 compare](https://github.com/michaelxzhang/kdiff3/blob/master/kdiff3cmp.PNG)

===============================================================================================================================
KDiff3-Readme
=============

Author: Joachim Eibl  (joachim.eibl at gmx.de)
Copyright: (C) 2002-2014 by Joachim Eibl
KDiff3-Version: 0.9.98

KDiff3 runs best on KDE but can be built without it, depending only on Qt-libs.
These are available for Un*x, Windows, Mac.
Thus there are many setup possibilities to consider.

Supported Qt-versions: 4.8, 5.2 or higher.
Supported KDE-version: 4
(For KDE3/Qt3 use KDiff3-0.9.92 or older.)

Contents
--------

- Introduction
- License
- Requirements & Installation
  - For KDE4
  - With Qt4-libs, without KDE
    - for Linux/Un*x
    - for Windows
    - Debugging with MinGW under Windows:
    - for Mac: Building KDiff3 for Mac OSX (with Intel processor)
    - Creating and installing translation messages
- Additional hints


Introduction
------------

KDiff3 is a program that
- compares and merges two or three input files or directories,
- shows the differences line by line and character by character (!),
- provides an automatic merge-facility and
- an integrated editor for comfortable solving of merge-conflicts
- has support for KDE-KIO (ftp, sftp, http, fish, smb),
- has an intuitive graphical user interface,
- provides a context menu for KDE-Konqueror and Windows-Explorer,
- supports 64 bit systems. (Some build issues are discussed in here.)
- Support for many encodings and Unicode.

Do you want help translating? Read the README in the po-subdirectory!


License
-------

    GNU GENERAL PUBLIC LICENSE, Version 2, June 1991
    This program is free software; you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation; either version 2 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program; if not, write to the Free Software
    Foundation, Inc., 51 Franklin Steet, Fifth Floor, Boston, MA 02111-1307
    USA

    For details see file "COPYING".


Build & Install (for Un*x systems)
----------------------------------

0) Unpack KDiff3*.tar.gz
1) Run "./configure kde4" or "./configure qt4" from the KDiff3 source directory.
2) Follow instructions
If it doesn't work continue reading.


Requirements & Installation
---------------------------

- for KDE4:
   For installation on most distributions you usually also need these packages
   (names as on opensuse):
   - g++ (version 4.2 or newer)
   - libqt4-devel (Qt4-libs, version 4.8.0 or newer)
   - libkde4-devel (KDE4 Header files and development libraries)
   - libkonq-devel (optional, needed for the kdiff3-plugin, if not installed
                    then the contextmenu plugin for konqueror won't be built.)
   - cmake (>2.6, checks dependencies and creates the appropriate Makefiles for
     your system)

   Typically in a terminal (e.g. konsole) you cd into the kdiff3-directory and
   run "./configure kde4". This script is essentially the same as these commands:

      mkdir releaseKde
      cd releaseKde
      # Find out your KDE4-directory and note the result
      kde4-config --prefix
      # create Makefile, replace <KDE4-prefix> with the prior result
      cmake .. -DCMAKE_INSTALL_PREFIX=<KDE4-prefix>
      # run make (compile and link)
      make
      # install as root user
      sudo make install

   Now KDiff3 should be ready to use. Type "kdiff3" to start it.
   There should also be a entry in your KDE-start menu in
   "(Applications->)Development".

   For creating a debug version:
      mkdir debug
      cd debug
      # Find out your KDE4-directory and note the result
      kde4-config --prefix
      cmake .. -DCMAKE_INSTALL_PREFIX=<KDE4-prefix> -DCMAKE_BUILD_TYPE=debugfull
      make
      sudo make install

   The <KDE4-prefix> depends on your distribution:
   The command "kde4-config --prefix" should tell you.
   - For opensuse 12 use "/usr".

- Building KDiff3 with Qt4-libs, but without KDE
    - for Linux/Un*x
    - for Windows
    - for Mac

   The version 0.9.98 requires Qt 4.8.0 or newer (from http://qt-project.org/) for
   compilation.

   Recommended: Get Qt with QtCreator and use the kdiff3.pro file in src-QT4.
                (should also work with Qt5)

   From command line: Install a working set of Qt-libs.
   Build-instructions (Un*x, Linux, Mac):
    Assuming Qt is correctly installed run "./configure qt4" which essentially
    does the same as:
    - mkdir releaseQt
    - cd releaseQt
    - qmake ../src-QT4/kdiff3.pro
    - make (or "gmake", or "mingw32-make" etc.)

  Debugging with MinGW under Windows:
    - Use Qt Creator as debugger frontend!

  Building KDiff3 (Qt4) for Mac OSX:
    1) Install XCode
    2) Install Qt with QtCreator for Mac
    3) Proceed again by opening the kdiff3.pro file

  Creating and installing the translation messages
    The po directory contains translations from the KDE-translation teams.
    If you use the Qt-only-version of KDiff3, then the installation described
    above won't install translations automatically.
    To create and install the translations:
    1) cd .../kdiff3-0.9.98/po
    2) sh create_qm_files install    (asks for a super user password)
    Just to create the files in the po directory (as needed for the windows
    version):
    2) sh create_qm_files local


(End of KDiff3 with Qt4-instructions)
------------------------------------------------------------------------

Additional hints
----------------

   Start from commandline:
   - Comparing 2 files:     kdiff3 file1 file2
   - Merging 2 files:       kdiff3 file1 file2 -o outputfile
   - Comparing 3 files:     kdiff3 file1 file2 file3
   - Merging 3 files:       kdiff3 file1 file2 file3 -o outputfile
        Note that file1 will be treated as base of file2 and file3.

   If all files have the same name but are in different directories, you can
   reduce typework by specifying the filename only for the first file. E.g.:
   - Comparing 3 files:     kdiff3 dir1/filename dir2 dir3
   (This also works in the open-dialog.)

   If you start without arguments, then a dialog will appear where you can
   select your files via a filebrowser.

   For more documentation, see the help-menu or the subdirectory doc.

   Have fun!
