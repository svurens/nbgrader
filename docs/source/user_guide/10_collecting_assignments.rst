
Collecting assignments
======================

.. seealso::

    :doc:`/command_line_tools/nbgrader-collect`
        Command line options for ``nbgrader fetch``

    :doc:`/command_line_tools/nbgrader-list`
        Command line options for ``nbgrader list``

After students have submitted their assignments, the instructor can view
what has been submitted with ``nbgrader list --inbound``:

.. code:: python

    %%bash
    
    nbgrader list --inbound


.. parsed-literal::

    [ListApp | INFO] Submitted assignments:
    [ListApp | INFO] example_course travis Problem Set 1 2015-06-23 16:01:22 UTC
    [ListApp | INFO] example_course travis Problem Set 1 2015-06-23 16:01:25 UTC


The instructor can then collect all submitted assignments with
``nbgrader collect`` and passing the name of the assignment:

.. code:: python

    %%bash
    
    nbgrader collect "Problem Set 1"


.. parsed-literal::

    [CollectApp | INFO] Collecting submission: travis Problem Set 1


This will copy the student submissions to the ``submitted`` folder in a
way that is automatically compatible with ``nbgrader autograde``:

.. code:: python

    %%bash
    
    ls -l submitted


.. parsed-literal::

    total 0
    drwxrwxr-x 3 travis travis 60 Jun 23 16:00 Bitdiddle
    drwxrwxr-x 3 travis travis 60 Jun 23 16:00 Hacker
    drwxrwxr-x 3 travis travis 60 Jun 23 16:01 travis

