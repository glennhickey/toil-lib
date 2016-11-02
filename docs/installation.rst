Installation
============

Prerequisites
-------------

* Python 2.7.x

* pip_ > 7.x

* Toil 3.3.0 or later

.. _pip: https://pip.readthedocs.org/en/latest/installing.html

Basic installation
------------------

To set up a basic toil-lib installation use

::

    pip install toil-lib


Building & testing
------------------

It is recommended that development on Toil and toil-lib be done inside a
virtualenv. Using a virtualenv isolates Toil dependencies to prevent dependency
conflicts and limits the scope of what is deployed during hot-deployment.
Documentation on installing virtualenv can be found here_.

.. _here: https://virtualenv.pypa.io/en/stable/installation/

After cloning the source and ``cd``-ing into the project root, create a
virtualenv and activate it::

    virtualenv venv
    . venv/bin/activate

Simply running

::

   make

from the project root will print a description of the available Makefile
targets.

Once you created and activated the virtualenv, the first step is to install the
build requirements. These are additional packages that toil-lib needs to be tested
and built, but not run::

   make prepare

Once the virtualenv has been prepared with the build requirements, running

::

   make develop

will create an editable installation of toil-lib and its runtime requirements in
the current virtualenv. The installation is called *editable* (also known as a
`development mode`_ installation) because changes to the toil-lib source code
immediately affect the virtualenv.

.. _development mode: https://pythonhosted.org/setuptools/setuptools.html#development-mode

"IIRC, toil-lib make develop will not install toil. I would note this and link back to the toil install docs."

To build the docs, run ``make develop`` followed by

::

    make docs

To invoke the tests (unit and integration) use

::

   make test

Run an individual test with

::

   make test tests=src/toil_lib/test/test_files.py::test_copy_files

The default value for ``tests`` is ``"src"`` which includes all tests in the
``src`` subdirectory of the project root.
