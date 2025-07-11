Installation
============

Expyriment works with `Python`_ 3 (>=3.9).


Dependencies
------------

Expyriment depends on the following Python packages:

* Pygame_ (>=2.5.2,<3)
* PyOpenGL_ (>=3, <4)
* NumPy_ (>=1.6,<3)
* mediadecoder_ (>=0.2.3,<1)=
* PySerial_ (>=3.0,<4)
* PyParallel_ (>=0.2,>1)

Please be aware that Expyriment plugins (extras) might have further dependencies.


Installing Expyriment
---------------------

Expyriment (and its dependencies) can be installed with:

::

    pipx install expyriment

or

::
    
    pip install expyriment


Platform-specific instructions
------------------------------

We provide more detailed platform-specific instructions for installing 
Expyriment here:

.. toctree::
   :maxdepth: 1
   :titlesonly:

   Windows <Installation.Windows>
   macOS <Installation.macOS>
   Linux <Installation.Linux>
   Android <Installation.Android>


.. _Python: https://www.python.org/
.. _Pygame: https://www.pygame.org/
.. _PyOpenGl: https://pyopengl.sourceforge.net/
.. _mediadecoder: https://dschreij.github.io/projects/python-mediadecoder
.. _PyParallel: https://github.com/pyserial/pyparallel
.. _PySerial: https://github.com/pyserial/pyserial
.. _Numpy: https://numpy.org/
.. _inpout32: https://www.highrez.co.uk/Downloads/InpOut32/
.. _dlportio: https://real.kiev.ua/2010/11/29/dlportio-and-32-bit-windows/
