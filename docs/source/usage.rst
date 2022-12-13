Usage
=====

.. _installation:

Installation
------------

Requirements for Mac:

.. code-block:: console

   (.venv) $ pip install lumache
   (.venv) $ pip3 install --extra-index-url https://google-coral.github.io/py-repo/ tflite_runtime	
   (.venv) $ pip install pandas
   (.venv) $ pip install psycopg2-binary
   (.venv) $ pip install pillow
   (.venv) $ pip install kivymd
   (.venv) $ pip install matplotlib
   (.venv) $ pip install twilio


Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

