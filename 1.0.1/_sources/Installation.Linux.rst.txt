.. _Linux:

Platform-specific instructions: Linux
=====================================

There are multiple ways to install Expyriment. The recommended methods
require an active internet connection. If you need to install Expyriment on
a computer that has no internet connection (like lab computer), please use the
offline method.


Recommended
-----------

Using pipx
~~~~~~~~~~

The most convenient way to install Expyriment is via `pipx`_.
This installs Expyriment as an application in an isolated virtual environment.
After installation you can use Expyriment through the :doc:`CommandLineInterface`.

1. Use your distribution's package manager to install:

   * `python3` (if not already installed)
   * `pipx`

   For example, in Debian, run in a terminal:
   ::

       sudo apt install python3 pipx

2. To install Expyriment, run in a terminal:
   ::

       pipx install expyriment
       pipx ensurepath

Using pip
~~~~~~~~~

1. Use your distribution's package manager to install:

   * `python3` (if not already installed)
   * `python3-venv`

   For example, in Debian, run in a terminal:
   ::

       sudo apt install python3 python3-venv

2. To create (and activate) a `virtual environment`_, run in a terminal:
   ::

       python3 -m venv xpy-env
       source xpy-env/bin/activate

3. To install Expyriment, run in a terminal:
   ::

       pip install -U pip
       pip install expyriment


Offline
-------

If you don't have an internet connection on the computer you want to install Expyriment on,
you can download the necessary packages on a different computer that has, and then transfer
them to the target computer and install them there.
After installation your can use Expyriment like any other Python package.

**On an computer with internet connection (same OS, architecture and Python version!)**

1. Use your distribution's package manager to install:

   * `python3`
   * `python3-pip`

   For example, in Debian, run in a terminal:
   ::

       sudo apt install python3 pipx

2. To download Expyriment and dependencies into a directory ``Expyriment_Installation``, run in a terminal:
   ::

       mkdir Expyriment_Installation
       python3 -m pip download -d Expyriment_Installation expyriment

3. Copy the directory ``Expyriment_Installation`` to a portable storage device


**On the target computer**

1. Refer to your distribution's documentation on how to install the following packages offline:

   * `python3`
   * `python3-venv`

2. Copy the directory ``Expyriment_Installation`` from the portable storage device to the target computer

3. To create (and activate) a `virtual environment`_, run in a terminal:
   ::

       python3 -m venv xpy-env
       source xpy-env/bin/activate

4. To install Expyriment, run in a terminal:
   ::

       pip install --no-index --find-links Expyriment_Installation expyriment


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
    

.. _`pipx`: https://pipx.pypa.io
.. _`virtual environment`: https://docs.python.org/3/tutorial/venv.html
