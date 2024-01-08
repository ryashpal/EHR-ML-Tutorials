Install
=======

Follow the below steps to install EHR-ML in your computer.


Login
------

Upon login to a system and opening a terminal, the following prompt should appear, where the ``user`` is the user name and the ``hostname`` is the hostname of the system.

.. code-block:: console

   user@hostname:~$


Change directory
----------------

From the home directory which will be open by default, change to a suitable directory on your computer where the utility needs to be installed. For example, in this tutorial we have changed to ``workspace`` directory.

.. code-block:: console

   user@hostname:~$ cd workspace


Clone
-----

In the destination folder, clone the current version of EHR-ML repository from the GitHub.

.. code-block:: console

   user@hostname:~/workspace$ git clone https://github.com/ryashpal/EHR-ML.git


Open EHR-QC
-----------

Open the ``EHR-ML`` directory that is downloaded from GitHub after cloning.

.. code-block:: console

   user@hostname:~/workspace$ cd EHR-ML


Python virtual environment
--------------------------

The Python virtual environment encaptulates all the libraries required for the EHR-ML. All the necessary libraries listed in a requirements.txt file that can be found at the root of the repository. Below are the instructions to create and install dependancies in the Python virtual environment.

.. note::
   ``EHR-ML`` requires ``Python version 3.9`` or higher. For installing Python, please refer the below link: https://www.python.org/downloads/


Create virtual environment
~~~~~~~~~~~~~~~~~~~~~~~~~~

Inside the ``EHR-ML`` directory, create a new Python virtual enviroment to conveniently manage all the dependencies required for the utility.

.. code-block:: console

   user@hostname:~/workspace/EHR-ML$ python3 -m venv .venv


Activate virtual environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After creating the Python virtual enviroment, activate the virtual enviroment to start using it for subsequent commands. The prompt will change with ``(.venv)`` appearing in front of it as shown below;

.. code-block:: console

   user@hostname:~/workspace/EHR-ML$ source .venv/bin/activate
   (.venv) user@hostname:~/workspace/EHR-ML$


Install dependencies
~~~~~~~~~~~~~~~~~~~~

Install all the required dependencies listed in the requirements.txt file in the newly created Python virtual environment.

.. code-block:: console

   (.venv) user@hostname:~/workspace/EHR-ML$ pip install -r requirements.txt


Verify
~~~~~~

Verify the installation by running the following command. The expected output should contain ``EHR-ML <version number>``.

.. code-block:: console

   (.venv) user@hostname:~/workspace/EHR-ML$ python -m EHR-ML -v
   EHR-ML 1.0
