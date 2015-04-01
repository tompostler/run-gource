# run-gource

A collection of tools, scripts, guides, and code needed to run gource on a headless linux server (developed on Ubuntu 14.04)

    git clone git://source.ffmpeg.org/ffmpeg.git
    apt-get install libx264 libx264-dev
    cd ffmpeg/
    ./configure --enable-libx264 --enable-gpl
    make
    make install
    cd ..
    git clone git@github.com:acaudwell/Gource.git gource
    cd gource/
    ./autogen.sh
    ./configure
    make
    make install
