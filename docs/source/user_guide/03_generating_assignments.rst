
Releasing an assignment
=======================

.. seealso::

    :doc:`/command_line_tools/nbgrader-assign`
        Command line options for ``nbgrader assign``
        
    :doc:`01_philosophy`
        Details about how the directory hierarchy is structured

After an assignment has been created with the assignment toolbar, you will want to create a release version of the assignment for the students. As described in :doc:`01_philosophy`, you need to organize your files in a particular way. For releasing assignments, you should have the master copy of your files saved (by default) in the following directory structure:

::

    source/{assignment_id}/{notebook_id}.ipynb

(Note: here, the ``student_id`` is not included, because there is only
one master version for all students, and only one release version for
all students).

After running ``nbgrader assign``, the release version of the notebooks
will be:

::

    release/{assignment_id}/{notebook_id}.ipynb

As the instructor, you will need to provide your own infrastructure for
actually getting this release version to students.

Example
-------

In the following example, we have an assignment with two notebooks:

-  `source/Problem Set 1/Problem
   1.ipynb <source/Problem%20Set%201/Problem%201.html>`_
-  `source/Problem Set 1/Problem
   2.ipynb <source/Problem%20Set%201/Problem%202.html>`_

Before we can create the release version, we first need to set up the
database. We'll use the default database url, which is just to a sqlite
database called ``gradebook.db`` in the current directory. At this
point, all we need to do is just add the assignment to the database;
we'll also include a due date for it:

.. code:: python

    import os
    
    # remove an existing database
    if os.path.exists("gradebook.db"):
        os.remove("gradebook.db")
    
    # create a connection to the db using the nbgrader API
    from nbgrader.api import Gradebook
    gb = Gradebook("sqlite:///gradebook.db")
    
    # add the assignment to the database
    gb.add_assignment("Problem Set 1", duedate="2015-02-01 15:00:00.000000 PST")




.. parsed-literal::

    Assignment<Problem Set 1>



Now that we have the gradebook setup, we can actually run
``nbgrader assign``. Note that we need to pass it the name of the
assignment (which is "Problem Set 1"). We also specify that a *header*
notebook (``source/header.ipynb``) should be preprended to the beginning
of each notebook in the assignment:

.. code:: python

    %%bash
    
    nbgrader assign "Problem Set 1" --IncludeHeaderFooter.header=source/header.ipynb


.. parsed-literal::

    [AssignApp | INFO] Created profile dir: '/home/travis/.ipython/profile_nbgrader'
    [AssignApp | INFO] Linking source/./Problem Set 1/jupyter.png -> release/./Problem Set 1/jupyter.png
    [AssignApp | INFO] Converting notebook source/./Problem Set 1/Problem 2.ipynb to notebook
    [AssignApp | INFO] Writing 2517 bytes to release/./Problem Set 1/Problem 2.ipynb
    [AssignApp | INFO] Converting notebook source/./Problem Set 1/Problem 1.ipynb to notebook
    [AssignApp | INFO] Writing 8082 bytes to release/./Problem Set 1/Problem 1.ipynb
    [AssignApp | INFO] Setting destination file permissions to 644


After doing this, there will be a new folder called ``release`` with the
same structure as ``source``, but with the actual release version of the
files:

-  `release/Problem Set 1/Problem
   1.ipynb <release/Problem%20Set%201/Problem%201.html>`_
-  `release/Problem Set 1/Problem
   2.ipynb <release/Problem%20Set%201/Problem%202.html>`_
