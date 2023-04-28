# run-gource

A collection of tools, scripts, guides, and code needed to run gource on a headless linux server.

Developed on Ubuntu 14.04, verified most recently on Windows Server 2022 with WSL Ubuntu 20.04.5 LTS.

## Installation

In order to get gource, xvfb, and ffmpeg installed, follow the following steps.
`$` denotes a command that can be run as the local user.
`#` denotes a command that needs to be run as the root user (generally using `sudo`).
    
    $ git clone git@github.com:tompostler/run-gource.git
    $ git submodule update --init --recursive

    # apt install build-essential libx264-dev libx265-dev libnuma-dev pkg-config yasm
    
    $ cd ffmpeg/
    $ ./configure --enable-gpl --enable-libx264 --enable-libx265
    $ make
    # make install
    
    # apt install autoconf libfreetype6-dev libpcre3-dev libglew-dev libsdl2-dev libsdl2-image-dev libboost-filesystem-dev libglm-dev
    
    $ cd ..
    $ cd gource/
    $ ./autogen.sh
    $ ./configure
    $ make
    # make install
    
    # apt install xvfb xfonts-base xfonts-75dpi xfonts-100dpi xfonts-cyrillic libavcodec-extra

## Execution

A sample invocation chaining the two programs together:

    $ xvfb-run -a -s "-screen 0 1920x1080x24" gource -1920x1080 --stop-at-end --auto-skip-seconds 2 --seconds-per-day 0.25 --file-idle-time 0 --background-colour 000000 --title "Repo Name" --font-size 16 --key --user-image-dir .git/avatars/ --hide mouse,progress --output-ppm-stream - --output-framerate 30 | ffmpeg -y -r 30 -f image2pipe -vcodec ppm -i - -vcodec libx264 -preset medium -pix_fmt yuv420p -crf 20 -threads 0 -bf 0 /path/to/output/file.mp4 
