
Submitting assignments
======================

.. seealso::

    :doc:`/command_line_tools/nbgrader-submit`
        Command line options for ``nbgrader fetch``

    :doc:`/command_line_tools/nbgrader-list`
        Command line options for ``nbgrader list``

After working on an assignment, the student can submit their version for
grading using ``nbgrader submit`` and passing the name of the assignment
and the name of the class:

.. code:: python

    %%bash
    export HOME=/tmp/student_home && cd $HOME
    
    nbgrader submit "Problem Set 1" "example_course"


.. parsed-literal::

    [SubmitApp | INFO] Source: /tmp/student_home/Problem Set 1
    [SubmitApp | INFO] Destination: /tmp/exchange/example_course/inbound/travis+Problem Set 1+2015-06-24 12:20:37 UTC
    [SubmitApp | INFO] Submitted as: example_course Problem Set 1 2015-06-24 12:20:37 UTC


Students can see what assignments they have submitted using
``nbgrader list --inbound``:

.. code:: python

    %%bash
    export HOME=/tmp/student_home && cd $HOME
    
    nbgrader list "example_course" --inbound


.. parsed-literal::

    [ListApp | INFO] Submitted assignments:
    [ListApp | INFO] example_course travis Problem Set 1 2015-06-24 12:20:37 UTC


Importantly, students can run ``nbgrader submit`` as many times as they
want, and all submitted copies of the assignment will be preserved:

.. code:: python

    %%bash
    export HOME=/tmp/student_home && cd $HOME
    
    nbgrader submit "Problem Set 1" "example_course"


.. parsed-literal::

    [SubmitApp | INFO] Source: /tmp/student_home/Problem Set 1
    [SubmitApp | INFO] Destination: /tmp/exchange/example_course/inbound/travis+Problem Set 1+2015-06-24 12:20:40 UTC
    [SubmitApp | INFO] Submitted as: example_course Problem Set 1 2015-06-24 12:20:40 UTC


We can see all versions that have been submitted by again running
``nbgrader list --inbound``:

.. code:: python

    %%bash
    export HOME=/tmp/student_home && cd $HOME
    
    nbgrader list "example_course" --inbound


.. parsed-literal::

    [ListApp | INFO] Submitted assignments:
    [ListApp | INFO] example_course travis Problem Set 1 2015-06-24 12:20:37 UTC
    [ListApp | INFO] example_course travis Problem Set 1 2015-06-24 12:20:40 UTC

