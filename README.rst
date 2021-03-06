Deform Demo
===========

Demonstration application for the `Deform
<http://docs.pylonsproject.org/projects/deform/dev/>`_ Python HTML form
library.  Please see http://deformdemo.repoze.org for a running version
of this application.

Running the Demo
----------------

- Create a virtualenv::

    $ virtualenv2.7 --no-site-packages /path/to/my/venv

  Hereafter ``/path/to/my/venv`` will be referred to as $VENV in steps
  below.

- Get a checkout of deformdemo::

    $ git clone git://github.com/Pylons/deformdemo.git

- ``cd`` to the newly checked out deformdemo package::

    $ cd deformdemo

- Run ``setup.py dev`` using the virtualenv's ``python`` command::

    $ $VENV/bin/python setup.py dev

- While your working directory is still ``deformdemo``, start the demo
  application::

    $ $VENV/bin/pserve demo.ini

- Visit http://localhost:8522 in a browser to see the demo.

Running the Demo's Selenium Tests
---------------------------------

The ``deformdemo`` application serves as a target for functional
testing during Deform's development.  A suite of Selenium tests may be
run against a local instance of the demonstration application.  It is
wise to run these tests before submitting a patch.  Here's how:

- Start the ``deformdemo`` application as described above in "Running
  the Demo".  Leave the terminal window running this application open,
  and open another terminal window to perform the below steps.

- In the other terminal window, cd to the "deformdemo" checkout directory
  you created above in "Running the Demo"::

   $ cd /path/to/my/deformdemo/checkout

- Run the tests::

   $ $VENV/bin/nosetests

  ``$VENV`` is defined as it was in "Running the Demo" above.

- You will (hopefully) see Firefox pop up and it will begin to display in quick
  succession the loading of pages in the bottom window and some test output in
  the top window.  The tests will run for five or ten minutes.

- Test success means that the console window on which you ran
  ``nosetests`` shows a bunch of dots, a test summary, then ``OK``.  If
  it shows a traceback, ``FAILED``, or anything other than a straight
  line of dots, it means there was an error.

- Fix any errors by modifying your code or by modifying the tests to
  expect the changes you've made.

Testing an Alternate Renderer Implementation
--------------------------------------------

- Copy the ``demo.ini`` file from this demo package to your renderer's
  package.

- Change the ``deform.renderer`` key in the ``demo.ini`` copy to point at
  your renderer (it's a Python dotted name).

- Run ``pserve /path/to/your/copy/of/demo.ini``.

- Run the selenium tests as above.
