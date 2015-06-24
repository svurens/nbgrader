
Autograde a students' solution
==============================

.. seealso::

    :doc:`/command_line_tools/nbgrader-autograde`
        Command line options for ``nbgrader autograde``
        
    :doc:`01_philosophy`
        Details about how the directory hierarchy is structured

After assignments have been submitted by students, you will want to save them into a ``submitted`` directory. As described in :doc:`01_philosophy`, you need to organize your files in a particular way. For autograding assignments, you should have the submitted versions of students' assignments organized as follows:

::

    submitted/{student_id}/{assignment_id}/{notebook_id}.ipynb

After running ``nbgrader autograde``, the autograded version of the
notebooks will be:

::

    autograded/{student_id}/{assignment_id}/{notebook_id}.ipynb

Example
-------

In the following example, we have an assignment with two notebooks.
There are two submissions of the assignment:

Submission 1:

-  `submitted/Bitdiddle/Problem Set 1/Problem
   1.ipynb <submitted/Bitdiddle/Problem%20Set%201/Problem%201.html>`_
-  `submitted/Bitdiddle/Problem Set 1/Problem
   2.ipynb <submitted/Bitdiddle/Problem%20Set%201/Problem%202.html>`_

Submission 2:

-  `submitted/Hacker/Problem Set 1/Problem
   1.ipynb <submitted/Hacker/Problem%20Set%201/Problem%201.html>`_
-  `submitted/Hacker/Problem Set 1/Problem
   2.ipynb <submitted/Hacker/Problem%20Set%201/Problem%202.html>`_

Before we can actually start grading, we need to actually record who the
students are. We can do this using the API provided by nbgrader, which
provides access to a database to store information about students and
their grades:

.. code:: python

    # create a connection to the db using the nbgrader API
    from nbgrader.api import Gradebook
    gb = Gradebook("sqlite:///gradebook.db")
    
    # add some students to the database
    gb.add_student("Bitdiddle", first_name="Ben", last_name="Bitdiddle")
    gb.add_student("Hacker", first_name="Alyssa", last_name="Hacker")
    gb.add_student("Reasoner", first_name="Louis", last_name="Reasoner")




.. parsed-literal::

    Student<Reasoner>



Note: the assignment should also already be in the database. An example of how to add it is given in :doc:`03_generating_assignments`.

Once the database has been set up with the students, we can run the
autograder:

.. code:: python

    %%bash
    
    nbgrader autograde "Problem Set 1"


.. parsed-literal::

    [AutogradeApp | INFO] Linking submitted/Bitdiddle/Problem Set 1/jupyter.png -> autograded/Bitdiddle/Problem Set 1/jupyter.png
    [AutogradeApp | INFO] Linking submitted/Bitdiddle/Problem Set 1/timestamp.txt -> autograded/Bitdiddle/Problem Set 1/timestamp.txt
    [AutogradeApp | INFO] SubmittedAssignment<Problem Set 1 for Bitdiddle> submitted at 2015-02-02 14:58:23.948203
    [AutogradeApp | WARNING] SubmittedAssignment<Problem Set 1 for Bitdiddle> is 86303.948203 seconds late
    [AutogradeApp | INFO] Overwriting files with master versions from the source directory
    [AutogradeApp | INFO] Linking source/./Problem Set 1/jupyter.png -> autograded/Bitdiddle/Problem Set 1/jupyter.png
    [AutogradeApp | INFO] Sanitizing submitted/Bitdiddle/Problem Set 1/Problem 2.ipynb
    [AutogradeApp | INFO] Converting notebook submitted/Bitdiddle/Problem Set 1/Problem 2.ipynb to notebook
    [AutogradeApp | INFO] Writing 2560 bytes to autograded/Bitdiddle/Problem Set 1/Problem 2.ipynb
    [AutogradeApp | INFO] Autograding autograded/Bitdiddle/Problem Set 1/Problem 2.ipynb
    [AutogradeApp | INFO] Converting notebook autograded/Bitdiddle/Problem Set 1/Problem 2.ipynb to notebook
    [AutogradeApp | INFO] Executing notebook with kernel: python
    [AutogradeApp | INFO] Writing 2557 bytes to autograded/Bitdiddle/Problem Set 1/Problem 2.ipynb
    [AutogradeApp | INFO] Sanitizing submitted/Bitdiddle/Problem Set 1/Problem 1.ipynb
    [AutogradeApp | INFO] Converting notebook submitted/Bitdiddle/Problem Set 1/Problem 1.ipynb to notebook
    [AutogradeApp | WARNING] Checksum for grade cell correct_squares has changed!
    [AutogradeApp | WARNING] Checksum for grade cell squares_invalid_input has changed!
    [AutogradeApp | INFO] Writing 8134 bytes to autograded/Bitdiddle/Problem Set 1/Problem 1.ipynb
    [AutogradeApp | INFO] Autograding autograded/Bitdiddle/Problem Set 1/Problem 1.ipynb
    [AutogradeApp | INFO] Converting notebook autograded/Bitdiddle/Problem Set 1/Problem 1.ipynb to notebook
    [AutogradeApp | INFO] Executing notebook with kernel: python
    [AutogradeApp | INFO] Writing 21330 bytes to autograded/Bitdiddle/Problem Set 1/Problem 1.ipynb
    [AutogradeApp | INFO] Setting destination file permissions to 444
    [AutogradeApp | INFO] Linking submitted/Hacker/Problem Set 1/jupyter.png -> autograded/Hacker/Problem Set 1/jupyter.png
    [AutogradeApp | INFO] Linking submitted/Hacker/Problem Set 1/timestamp.txt -> autograded/Hacker/Problem Set 1/timestamp.txt
    [AutogradeApp | INFO] SubmittedAssignment<Problem Set 1 for Hacker> submitted at 2015-02-01 09:28:58.749302
    [AutogradeApp | INFO] Overwriting files with master versions from the source directory
    [AutogradeApp | INFO] Linking source/./Problem Set 1/jupyter.png -> autograded/Hacker/Problem Set 1/jupyter.png
    [AutogradeApp | INFO] Sanitizing submitted/Hacker/Problem Set 1/Problem 2.ipynb
    [AutogradeApp | INFO] Converting notebook submitted/Hacker/Problem Set 1/Problem 2.ipynb to notebook
    [AutogradeApp | INFO] Writing 2690 bytes to autograded/Hacker/Problem Set 1/Problem 2.ipynb
    [AutogradeApp | INFO] Autograding autograded/Hacker/Problem Set 1/Problem 2.ipynb
    [AutogradeApp | INFO] Converting notebook autograded/Hacker/Problem Set 1/Problem 2.ipynb to notebook
    [AutogradeApp | INFO] Executing notebook with kernel: python
    [AutogradeApp | INFO] Writing 2687 bytes to autograded/Hacker/Problem Set 1/Problem 2.ipynb
    [AutogradeApp | INFO] Sanitizing submitted/Hacker/Problem Set 1/Problem 1.ipynb
    [AutogradeApp | INFO] Converting notebook submitted/Hacker/Problem Set 1/Problem 1.ipynb to notebook
    [AutogradeApp | INFO] Writing 8871 bytes to autograded/Hacker/Problem Set 1/Problem 1.ipynb
    [AutogradeApp | INFO] Autograding autograded/Hacker/Problem Set 1/Problem 1.ipynb
    [AutogradeApp | INFO] Converting notebook autograded/Hacker/Problem Set 1/Problem 1.ipynb to notebook
    [AutogradeApp | INFO] Executing notebook with kernel: python
    [AutogradeApp | INFO] Writing 9501 bytes to autograded/Hacker/Problem Set 1/Problem 1.ipynb
    [AutogradeApp | INFO] Setting destination file permissions to 444


When grading the submission for ``Bitdiddle``, you'll see some warnings
that look like "Checksum for grade cell correct\_squares has changed!".
What's happening here is that nbgrader has recorded what the *original*
contents of the grade cell ``correct_squares`` (when ``nbgrader assign``
was run), and is checking the submitted version against this original
version. It has found that the submitted version changed (perhaps this
student tried to cheat by commenting out the failing tests), and has
therefore overwritten the submitted version of the tests with the
original version of the tests.

You may also notice that there is a note saying "Problem Set 1 for
Bitdiddle is 86303.948203 seconds late". What is happening here is that
nbgrader is detecting a file in Bitdiddle's submission called
``timestamp.txt``, reading in that timestamp, and saving it into the
database. From there, it can compare the timestamp to the duedate of the
problem set, and compute whether the submission is at all late.

Once the autograding is complete, there will be new directories for the
autograded versions of the submissions:

Autograded submission 1:

-  `autograded/Bitdiddle/Problem Set 1/Problem
   1.ipynb <autograded/Bitdiddle/Problem%20Set%201/Problem%201.html>`_
-  `autograded/Bitdiddle/Problem Set 1/Problem
   2.ipynb <autograded/Bitdiddle/Problem%20Set%201/Problem%202.html>`_

Autograded submission 2:

-  `autograded/Hacker/Problem Set 1/Problem
   1.ipynb <autograded/Hacker/Problem%20Set%201/Problem%201.html>`_
-  `autograded/Hacker/Problem Set 1/Problem
   2.ipynb <autograded/Hacker/Problem%20Set%201/Problem%202.html>`_
