The Expyriment plugin system (extras)
=====================================

Usage
-----
The design, stimuli, io and misc packages can be extended with plugins
(additional classes) that can be accessed via the 'extras' namespace of each
package. Expyriment will look for installed plugins in the following
locations within the ``.expyriment/extras`` (or ``~expyriment/extras``)
directory located in the current user's home directory:

- ``expyriment_extras_design``
- ``expyriment_extras_stmuli``
- ``expyriment_extras_io``
- ``expyriment_extras_misc``

Any plugins found will be integrated into the *.extras* namespace of each
package (e.g. ``expyriment.stimuli.extras.DotCloud``).

There are three ways to import extras:

1. Import all extras in one go::

    import expyriment
    expyriment.import_all_extras()

2. Import all extras from a specific package::

    import expyriment
    import expyriment.stimuli.extras

3. Import a specific plugin::

    import expyriment
    from expyriment_stimuli_extras.dotcloud import DotCloud

Download plugins from stash
---------------------------
Several extra plugins can be found in the `Expyriment stash`_. When Expyriment
has been installed with the option ``download`` (or ``all``), all plugins can be 
downloaded automatically by calling::

    expyriment.misc.download_from_stash(content="extras")

Alternatively, you can use the `Command Line Interface`_::

    expyriment -D
    
Development
-----------
When developing extra plugins, please consider making them available publicly in
the `Expyriment stash`_, by creating a pull request.

Extra plugins are implemented as a class wrapped in a Python package, where the name of the
package is the the name of the class in lowercase.

Here is an overview of the structure of an example plugin:
::

       myextraplugin
       ├── __init__.py
       └── _myextraplugin.py

The file ``_myextraplugin.py`` contains the actual plugin class ``MyExtraPlugin``.

The ``__init__.py`` file contains an abstract class with the same name that exposes the
``__init__`` method and any potential static methods of the actual plugin class
for lazy-loading, so be sure to document it properly:

.. code-block:: python

    from abc import ABC


    class MyExtraPlugin(ABC):
        """Class docstring.""""

        def __init__(self, **args):
            """Init docstring"""

            from ._myextraplugin import MyExtraPlugin
            self.__class__ = MyExtraPlugin
            MyExtraPlugin.__init__(self, **args)

        @staticmethod
            def some_static_method(**args):
               """Static method docstring."""

               from ._myextraplugin import MyExtraPlugin
               return MyExtraPlugin.some_static_method(**args)

For design and misc extras this is all there is, but for io and stimuli plugins,
additional conventions need to be taken care of.

io.extras
~~~~~~~~~
IO plugins have to inherit from ``expyriment.io.Input`` or ``expyriment.io.Output``
or both. This means they can also inherit from any other io class.

stimuli.extras
~~~~~~~~~~~~~~
Stimulus plugins have to inherit from ``expyriment.stimuli.Stimulus``. This means
they can also inherit from any other stimulus class.
Additionally, every visual extra stimulus class (inherited from ``expyriment.stimuli.Visual``)
needs a ``_create_surface`` method that defines what happens when the stimulus is preloaded,
plotted or presented.


.. _`Expyriment stash`: https://github.com/expyriment/expyriment-stash
.. _`Command Line Interface`: CommandLineInterface.html
