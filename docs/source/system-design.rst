System Design
=============

.. include:: ./_sections/system-design/prms.rst
.. include:: ./_sections/system-design/drms.rst
.. include:: ./_sections/system-design/cnrms.rst
.. include:: ./_sections/system-design/pprms.rst
.. include:: ./_sections/system-design/arms.rst    


Error Responses
---------------

**404 Not Found:**

.. code-block:: json

    {
        "error": "User not found"
    }

**401 Unauthorized:**

.. code-block:: json

    {
        "error": "Invalid or missing token"
    }