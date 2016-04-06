The **npbackend** is a backend interface to Python/NumPy that translates NumPy array operations into a sequence of Python function calls. By implementing these Python functions, external libraries can accelerate NumPy array operations without any modifications to the user Python/NumPy code.

For now, **npbackend** is integrated with the `Bohrium <http://www.bh107.org>`_ project and cannot be installed separately (the source code can be found `here <https://github.com/bh107/bohrium/tree/master/bridge/npbackend>`_) but it is our intension to decouple **npbackend** out of `Bohrium <http://www.bh107.org>`_ to become a standalone project.

Get the documentation at http://npbackend.readthedocs.org

