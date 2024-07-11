.. _Linux:

Platform-specific instructions: Linux
=====================================

All Linux distributions
-----------------------

1. Use your distribution's package manager to install

  * Python3
  * setuptools
  * pip3
  * build-essential (or equivalent)
  * libffi-dev
  * python3-dev
  * PortAudio
  * ffmpeg (for enhanced video support, optional)

2. In a command line, run::

    sudo pip3 install -U pip wheel
    sudo pip3 install -U expyriment[all]
    
   (Omit ``[all]`` to install without additional optional features)

For example, in Debian run::

    sudo apt-get install python3 python3-pip python3-setuptools build-essential libffi-dev python3-dev libportaudio2 ffmpeg
    sudo pip3 install -U pip wheel
    sudo pip3 install -U expyriment[all]
    

Notes
-----
**Switch off desktop effects, when running an experiment**

    Several window managers nowadays come with a compositing engine to produce
    3D desktop effects. To get accurate timing of the visual stimulus
    presentation it is important to switch off desktop effects in your window
    manager!

**Switch off Triple-Buffering, when running an experiment**

    On some machines (e.g. with Intel video cards), triple-buffering is switched
    on by default. For proper timing, this needs to be set off in the Xorg config::

     Option      "TearFree"        "false"
     Option      "TripleBuffer"    "false"

    For Nvidia, this can often be set in the Nvidia setting tool, rather than in
    the Xorg configuration file.

**Expyriment might return a scaled screen under Wayland**

    When using Wayland instead of X11, Expyriment might return a scaled screen.
    This depends on the Wayland implementation, and how it handles XWayland applications.
    Often this can also be changed explicitely by the user. For instance, under KDE Plasma,
    there is a global setting in the display settings which will make Expyriment return an
    unscaled screen ("Legacy Applications (X11)" --> "Apply Scaling Themselves").
    
.. _`release page`: http://github.com/expyriment/expyriment/releases/latest
