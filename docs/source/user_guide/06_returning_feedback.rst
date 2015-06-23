
Returning feedback to students
==============================

.. seealso::

    :doc:`/command_line_tools/nbgrader-feedback`
        Command line options for ``nbgrader feedback``
        
    :doc:`01_philosophy`
        Details about how the directory hierarchy is structured

After assignments have been autograded and/or manually graded, they will located in the `autograded` directory (see :doc:`01_philosophy` for details):

::

    autograded/{student_id}/{assignment_id}/{notebook_id}.ipynb

After running ``nbgrader feedback``, HTML versions of these notebooks
will be saved to:

::

    feedback/{student_id}/{assignment_id}/{notebook_id}.html

Example
-------

In the following example, we have an assignment with two notebooks.
There are two submissions of the assignment that have been graded:

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

Generating feedback is fairly straigtforward:

.. code:: python

    %%bash
    
    nbgrader feedback "Problem Set 1"


.. parsed-literal::

    [FeedbackApp | INFO] Linking autograded/Bitdiddle/Problem Set 1/jupyter.png -> feedback/Bitdiddle/Problem Set 1/jupyter.png
    [FeedbackApp | INFO] Linking autograded/Bitdiddle/Problem Set 1/timestamp.txt -> feedback/Bitdiddle/Problem Set 1/timestamp.txt
    [FeedbackApp | INFO] Converting notebook autograded/Bitdiddle/Problem Set 1/Problem 1.ipynb to html
    [FeedbackApp | INFO] Writing 278935 bytes to feedback/Bitdiddle/Problem Set 1/Problem 1.html
    [FeedbackApp | INFO] Converting notebook autograded/Bitdiddle/Problem Set 1/Problem 2.ipynb to html
    [FeedbackApp | INFO] Writing 250504 bytes to feedback/Bitdiddle/Problem Set 1/Problem 2.html
    [FeedbackApp | INFO] Setting destination file permissions to 444
    [FeedbackApp | INFO] Linking autograded/Hacker/Problem Set 1/jupyter.png -> feedback/Hacker/Problem Set 1/jupyter.png
    [FeedbackApp | INFO] Linking autograded/Hacker/Problem Set 1/timestamp.txt -> feedback/Hacker/Problem Set 1/timestamp.txt
    [FeedbackApp | INFO] Converting notebook autograded/Hacker/Problem Set 1/Problem 1.ipynb to html
    [FeedbackApp | INFO] Writing 267605 bytes to feedback/Hacker/Problem Set 1/Problem 1.html
    [FeedbackApp | INFO] Converting notebook autograded/Hacker/Problem Set 1/Problem 2.ipynb to html
    [FeedbackApp | INFO] Writing 250634 bytes to feedback/Hacker/Problem Set 1/Problem 2.html
    [FeedbackApp | INFO] Setting destination file permissions to 444


Once the feedback has been generated, there will be new directories and
HTML files corresponding to each notebook in each submission:

Feedback for submission 1:

-  `feedback/Bitdiddle/Problem Set 1/Problem
   1.html <feedback/Bitdiddle/Problem%20Set%201/Problem%201.html>`_
-  `feedback/Bitdiddle/Problem Set 1/Problem
   2.html <feedback/Bitdiddle/Problem%20Set%201/Problem%202.html>`_

Feedback for submission 2:

-  `feedback/Hacker/Problem Set 1/Problem
   1.html <feedback/Hacker/Problem%20Set%201/Problem%201.html>`_
-  `feedback/Hacker/Problem Set 1/Problem
   2.html <feedback/Hacker/Problem%20Set%201/Problem%202.html>`_
