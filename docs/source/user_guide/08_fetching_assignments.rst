
Fetching assignments
====================

.. seealso::

    :doc:`/command_line_tools/nbgrader-fetch`
        Command line options for ``nbgrader fetch``

    :doc:`/command_line_tools/nbgrader-list`
        Command line options for ``nbgrader list``

From the student's perspective, they can list what assignments have been
released, and then fetch a copy of the assignment to work on. First,
we'll create a temporary directory to represent the student's home
directory:

.. code:: python

    %%bash
    
    # remove the fake student home directory if it exists, for demo purposes
    rm -rf /tmp/student_home
    
    # create the fake student home directory and switch to it
    mkdir /tmp/student_home

If you are not using the default exchange directory (as is the case
here), you will additionally need to provide your students with a
configuration file that sets the appropriate directory for them:

.. code:: python

    %%file /tmp/student_home/nbgrader_config.py
    
    c = get_config()
    c.TransferApp.exchange_directory = '/tmp/exchange'


.. parsed-literal::

    Writing /tmp/student_home/nbgrader_config.py


From the student's perspective, they can see what assignments have been
released using ``nbgrader list``, and passing the name of the class:

.. code:: python

    %%bash
    export HOME=/tmp/student_home && cd $HOME
    
    nbgrader list "example_course"


.. parsed-literal::

    [ListApp | INFO] Created profile dir: '/tmp/student_home/.ipython/profile_nbgrader'
    [ListApp | INFO] Released assignments:
    [ListApp | INFO] example_course Problem Set 1


They can then fetch an assignment for that class using
``nbgrader fetch`` and passing the name of the class and the name of the
assignment:

.. code:: python

    %%bash
    export HOME=/tmp/student_home && cd $HOME
    
    nbgrader fetch "example_course" "Problem Set 1"


.. parsed-literal::

    [FetchApp | INFO] Source: /tmp/exchange/example_course/outbound/Problem Set 1
    [FetchApp | INFO] Destination: /tmp/student_home/Problem Set 1
    [FetchApp | INFO] Fetched as: example_course Problem Set 1


Running ``nbgrader fetch`` copies the assignment files from the exchange
directory to the local directory:

.. code:: python

    %%bash
    
    ls -l "/tmp/student_home/Problem Set 1"


.. parsed-literal::

    total 20
    -r--r--r-- 1 travis travis 5733 Jun 24 23:37 jupyter.png
    -rw-r--r-- 1 travis travis 8082 Jun 24 23:37 Problem 1.ipynb
    -rw-r--r-- 1 travis travis 2517 Jun 24 23:37 Problem 2.ipynb

