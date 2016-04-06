New Target
==========

In order to implement a new target for **npbackend**, we need to implement the functions in `interface.py <https://github.com/bh107/bohrium/blob/master/bridge/npbackend/target/interface.py>`_:

.. literalinclude:: code/interface.py
   :language: python

NumPy Example
-------------

An example of a target implementation is `target_numpy.py <https://github.com/bh107/bohrium/blob/master/bridge/npbackend/target/target_numpy.py>`_ that uses NumPy as a backend. Now, implementing a NumPy backend that targets NumPy does not make that much sense but it is a good example.

.. note:: In some cases using NumPy as a backend will output native NumPy because of memory allocation `reuse <http://curis.ku.dk/ws/files/126010515/Doubling.pdf>`_.


.. literalinclude:: code/target_numpy.py
   :language: python

Now, let’s try to run a small Python/NumPy example::

    import numpy as np

    a = np.ones(100000000)
    for _ in xrange(100):
        a = a + 42

First with native NumPy::

    time -p python tt.py
    real 26.69
    user 10.20
    sys 16.50

And then with **npbackend** using NumPy as backend::

    NPBE_TARGET="numpy" time -p python -m bohrium tt.py
    real 14.36
    user 14.02
    sys 0.34

Because of the memory allocation reuse, **npbackend** actually outperforms native NumPy. However, this is only the case because we allocate and free a significant number of large arrays.
