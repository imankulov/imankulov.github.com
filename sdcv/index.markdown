---
layout: default
title: sdcv - the sdcv subversion mirror with one helpful patch
projectname: / sdcv
projectpage: http://github.com/imankulov/sdcv/
regards: Mirror of the <a href="http://sdcv.sourceforge.net/">SDCV project</a>
projectlinks: 
---

**sdcv** subversion repository mirror with the set of [patches][patch] improving readline support (primarily autocompletion).

*Note:* sdcv is a console version of [StarDict][stardict] program

Deb-package for ubuntu has been built and uploaded to the [launchpad][]. 

### Installation instructions

#### Ubuntu intrepid

Append to `/etc/apt/sources.list`:

    deb http://ppa.launchpad.net/roman-imankulov/ubuntu intrepid main

then type:

    apt-get update
    apt-get install sdcv


#### Deb-based linux

Append to `/etc/apt/sources.list`:
    
    deb http://ppa.launchpad.net/roman-imankulov/ubuntu intrepid main

then get the sources and satisfy dependencies:

    mkdir sdcv-dev && cd sdcv-dev
    apt-get update
    apt-get build-dep sdcv
    apt-get source sdcv

then rebuild and install package:

    cd sdcv-<version>
    dpkg-buildpackage -rfakeroot -uc -us
    cd ..

if you were pretty lucky you get the `deb` package:

    apt-get install sdcv-*.dev

#### Alien linux distribution

[Download sources][tgz] and build it with `./configure && make && sudo make install` or whatever your distribution requires.

Before that you have to create `./configure` script with these commands:

    aclocal -I./m4
    autoconf 
    automake --add-missing

[patch]: http://sourceforge.net/tracker/?func=detail&aid=2826995&group_id=122858&atid=694730 "SDCV readline patch"
[tgz]: http://github.com/imankulov/sdcv/tarball/master 
[stardict]: http://stardict.sourceforge.net/
[launchpad]: https://launchpad.net/

