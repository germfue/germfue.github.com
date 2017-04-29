---
layout: post
title:  "Build Tor in Fedora 25"
published: true
tags: 
 - fedora
 - tor
priority: 0.8
---
First, checkout the repository:

    git clone https://git.torproject.org/tor.git

I would also recommend that you checkout the torguts repo, as it contains excellent documentation:

    git clone https://git.torproject.org/user/nickm/torguts.git

You will need these dependencies, in order to build Tor:

    # tools for compiling and linking
    sudo dnf groups install "C Development Tools and Libraries"
    # this is for the man pages
    sudo dnf install asciidoc
    # and these are the dependencies Tor relies on
    sudo dnf install libevent libevent-devel openssl openssl-devel zlib zlib-devel

To build, you just need 4 simple steps:

    cd tor
    ./autogen.sh
    ./configure
    make

Wait till it is ready and enjoy!
