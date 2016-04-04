# run-gource

A collection of tools, scripts, guides, and code needed to run gource on a headless linux server (developed on Ubuntu 14.04)

## Installation

In order to get gource, xvfb, and ffmpeg installed, follow the following steps.
`$` denotes a command that can be run as the local user. `#` denotes a command
that needs to be run as the root user (generally using `sudo`).
    
    $ git clone git@github.com:tompostler/run-gource.git
    $ git submodule update --init --recursive

    # apt-get install build-essential libx264-dev pkg-config yasm
    
    $ cd ffmpeg/
    $ ./configure --enable-libx264 --enable-gpl
    $ make
    # make install
    
    # apt-get install autoconf libfreetype6-dev libpcre3-dev libglew-dev libsdl2-dev libsdl2-image-dev libboost-filesystem-dev libglm-dev
    
    $ cd ..
    $ cd gource/
    $ ./autogen.sh
    $ ./configure
    $ make
    # make install
    
    # apt-get install xvfb xfonts-base xfonts-75dpi xfonts-100dpi xfonts-cyrillic libavcodec-extra
