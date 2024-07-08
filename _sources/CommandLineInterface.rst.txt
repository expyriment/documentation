Command line interface
======================

The Expyriment command line interface provides a convenient way to run
experiment scripts and apply default settings, as well as access to a selection
of other common functionality. Note: non-capitalized letter arguments are
(chainable) options, capitalized letter arguments run single commands.

Usage
-----

::
    
    expyriment [-h] [-0] [-1] [-2] [-3] [-a] [-d] [-f] [-i] [-t] [-w]
               [--display INDEX] [--display-resolution WIDTHxHEIGHT]
               [--opengl MODE] [--window-size WIDTHxHEIGHT] [-A] [-B] [-C] [-D]
               [-I] [-J] [-S] [-T] [SCRIPT]

    positional arguments:
      SCRIPT                the experiment script to be executed

    options:
      -h, --help            show this help message and exit
      -0, -g, --no-opengl   DEPRECATED: no OpenGL (no vsync / no blocking)
      -1, --no-blocking     DEPRECATED: OpenGL (vsync / no blocking)
      -2, --blocking        DEPRECATED: OpenGL (vsync / blocking)
      -3, --alternative-blocking
                            DEPRECATED: OpenGL (vsync / alternative blocking)
      -a, --auto-subject-id
                            auto create subject ID
      -d, --develop-mode    develop mode (equivalent to -wfat)
      -f, --fast-mode       fast mode (no initialize delay and fast quitting)
      -i, --intensive-logging
                            intensive logging (log level 2)
      -t, --no-time-stamps  no time stamps for output files
      -w, --window-mode     window mode
      --display INDEX       show the screen on specific display (multi-monitor
                            setting)
      --display-resolution WIDTHxHEIGHT
                            set the display resolution (only in fullscreen mode)
      --opengl MODE         set the OpenGL mode: 0 = No OpenGL (no vsync / no
                            blocking), 1 = OpenGL (vsync / no blocking), 2 = OpenGL
                            (vsync / blocking)
      --window-size WIDTHxHEIGHT
                            set the window size (only in window mode)
      -A, --Api             start the API reference tool
      -B, --Browser-api     open browser with API reference
      -C, --Create-exp      create experiment template
      -D, --Download-stash  download from Expyriment stash
      -I, --Interactive     start an interactive session
      -J, --Join-data       join data files to one single csv file
      -S, --System-info     print system information
      -T, --Test-suite      run the Expyriment test suite
