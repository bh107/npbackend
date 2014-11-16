Usage
=====

Using ``npbackend`` requires enabling the module and choosing a ``target``.

Enabling ``npbackend``
----------------------

The least intrusive method of enabling ``npbackend`` is invoking your Python
program with the module loaded. Which means instead of invoking your
Python/NumPy program like this::

  python my_program.py

You will invoke it like this instead::

  python -m npbackend my_program.py

Which will effectively overrule the ``numpy`` module and instead use
``npbackend``. That is all it takes.

Another approach is replacing your ``import numpy`` statements with ``import npbackend``. For example, replacing:

.. code-block:: python

   import numpy as np

With:

.. code-block:: python

   import npbackend as np

Choosing a ``npbackend`` target
-------------------------------

``npbackend`` will default to using Bohrium as the backend target. Changing
backend target is done via the ``NPBE_TARGET`` environment variable. Valid
values for ``NPBE_TARGET`` are:

1. bhc, the default targeting `Bohrium <http://bh107.org>`_
2. numexpr, targeting `Numexpr <https://github.com/pydata/numexpr>`_
3. pygpu, targeting `libgpuarray <http://deeplearning.net/software/libgpuarray/installation.html>`_
4. numpy, Using `NumPy <http://www.numpy.org/>`_ itself through NumPy backend, this is most likely not
   something you would want to do, the value is only provided for testing
   purposes.

If you which to use something else than the default target, then you can invoke
your Python/NumPy application with::

  NPBE_TARGET="numexpr" python -m npbackend my_program.py

Or if your changed import statements::

  NPBE_TARGET="numexpr" python my_program.py

That is all there is to it.
