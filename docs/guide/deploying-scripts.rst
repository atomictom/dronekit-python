.. _deploying-scripts:

==================
Deploying a Script
==================

Because DroneKit-Python is still under heavy development, you may find it beneficial to control which version you are using and have a plan for deployment.

This section includes some tips for using `virtualenvwrapper <https://virtualenvwrapper.readthedocs.org/en/latest/>`_ (an extension of `virtualenv <https://virtualenv.readthedocs.org/en/latest/>`_) to manage versioning and deployment.



Installing virtualenvwrapper
============================

First, please follow the instructions for installing DroneKit-Python on your platform of choice under the section :ref:`getting_started_installing_dronekit` in :ref:`get-started`:

* :ref:`getting_started_installing_dronekit_linux`
* :ref:`getting_started_installing_dronekit_mac`

.. note::

    virtualenvwrapper uses functionality specific to bash, a shell commonly used in Linux and Mac. To follow this guide on Windows you can use `cygwin <https://www.cygwin.com/>`_ or `look here for more information <http://stackoverflow.com/questions/2615968/installing-virtualenvwrapper-on-windows>`_.

After you have installed **pip** you can install virtualenvwrapper and its dependencies.

.. code-block:: bash

    sudo pip install virtualenvwrapper

Then, place

.. code-block:: bash

    source $(which virtualenvwrapper.sh)

into your shell startup file (most commonly **.bashrc**).



Working with virtualenvwrapper
==============================

Next, you will want to create a new virtual environment:

.. code:: bash

    mkvirtualenv my-dronekit-project

This will create a new virtual environment and activate it.

Next, you will want to install **dronekit** into your new virtual environment.

.. code:: bash

    pip install dronekit

If you need to install anything else, you can use ``pip install`` as usual.

.. tip::

    No ``sudo`` is required because the virtual environment is installed in your home directory and only effects instances of bash under your control.

When you are done working with your virtual environment, you can deactivate it to switch back to the global python environment with

.. code:: bash

    deactive

To work on it again use

.. code:: bash

   workon my-dronekit-project

.. note::

    You will need to use ``workon my-dronekit-project`` on each instance of bash you wish to run your code in.



Deployment and Version Control
==============================

At any point you can write a list of every library you have installed along with its version to file by using

.. code:: bash

    pip freeze > requirements.txt

Later, you can tell **pip** to install those libraries at the versions listed with

.. code:: bash

    pip install -r requirements.txt

By using multiple virtual environments you can easily test new versions of DroneKit without the risk of breaking your project. You can also tie a **requirements.txt** to each release of your project to guarantee the appropriate version of DroneKit and any other libraries are installed, and to speed up deployment. If you use version control, you can keep requirements.txt under your version control to make it easy to install the software appropriate to any given commit.
