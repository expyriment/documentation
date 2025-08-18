.. _macOS:

Platform-specific instructions: macOS
=====================================

There are multiple ways to install Expyriment. The recommended method
requires an active internet connection. If you need to install Expyriment on a
computer that has no internet connection (like lab computers), please use the
offline method. 


Recommended
-----------

Using pipx
~~~~~~~~~~

The most convenient way to install Expyriment is via `pipx`_.
This installs Expyriment as an application in an isolated virtual environment.
After installation you can use Expyriment through the :doc:`CommandLineInterface`.

1. Install `Python 3.13.5`_

2. To install pipx, run in a terminal:
   ::

       python3 -m pip install --user pipx

3. To install Expyriment, run in a terminal:
   ::

       pipx install expyriment
       pipx ensurepath

Using pip
~~~~~~~~~

The classical and more flexible way to install Exyriment is via pip.
This simply installs Expyriment as a library in a Python environment of your choice.
After installation you can use Expyriment like any other Python package.

1. Install `Python 3.13.5`_

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

1. On the Desktop, create a directory called ``Expyriment_Installation``

2. Download `Python 3.13.5`_ to  ``Expyriment_Installation``

3. To download Expyriment and dependencies into ``Expyriment_Installation``, run in a terminal:
   ::

       python3 -m pip download -d ~/Desktop/Expyriment_Installation expyriment
    
4. Copy the directory ``Expyriment_Installation`` from the Desktop to a portable storage device


**On the target computer**

1. Copy the directory ``Expyriment_Installation`` from the portable storage device to the Desktop

2. Install ``Expyriment_Installation/python-3.13.5-macos11.pkg``

3. To create (and activate) a `virtual environment`_, run in a terminal:
   ::

       python3 -m venv xpy-env
       source xpy-env/bin/activate

4. To install Expyriment, run in a terminal:
   ::

       pip install --no-index --find-links ~/Desktop/Expyriment_Installation expyriment


Notes
-----

**macOS does not report accurate visual presentation times**

    After the necessary switch to Pygame 2 that happened with Expyriment 1.0.0, macOS does not
    seem to be reporting accurate visual presentation times. macOS has a compositor running which
    cannot be turned off. In theory, fullscreen programmes should be able to bypass it automatically,
    however, this does not seem to be the case in our experience.
    While Expyriment on macOS will work perfecly fine for designing and implementing your experiments,
    we do not recommend to use macOS to run an actual experiment (i.e. test participants)!

**Do not start your experiments out of IDLE**

    If you are using the IDLE editor that comes with the Python installation, 
    be aware that IDLE itself is written in Python. Starting your Expyriment 
    programme out of IDLE (by clicking on "Run" or by pressing F5), might thus 
    lead to improper timing!

    We therefore strongly suggest to run Expyriment programmes from the command 
    line when testing participants.


.. _Python 3.13.5: https://www.python.org/ftp/python/3.13.5/python-3.13.5-macos11.pkg
.. _`pipx`: https://pipx.pypa.io
.. _`virtual environment`: https://docs.python.org/3/tutorial/venv.html
