# run-gource

A collection of tools, scripts, guides, and code needed to run gource on a headless linux server (developed on Ubuntu 14.04)
    
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
    
    # apt-get install xvfb
