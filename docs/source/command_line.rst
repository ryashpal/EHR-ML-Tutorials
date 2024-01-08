Command Line
============


Install
+++++++

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


Open EHR-ML
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
------

Verify the installation by running the following command. The expected output should contain ``EHR-ML <version number>``.

.. code-block:: console

   (.venv) user@hostname:~/workspace/EHR-ML$ python -m EHR-ML -v
   EHR-ML 1.0


EHR2Mortality
+++++++++++++

Evaluate
--------

This utility will help to evaluate the performance of mortality prediction model using 5-fold cross validation.

Help menu
~~~~~~~~~

To display the help menu of the Evaluate functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2mortality.Evaluate -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2mortality.Evaluate --help


Output

.. code-block:: console

   usage: Evaluate.py [-h] [-tc TARGET_COLUMN] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN] [-wb WINDOW_BEFORE] [-wa WINDOW_AFTER]
                      [-sp SAVE_PATH]
                      data_file
   
   EHR-ML machine learning utility
   
   positional arguments:
     data_file             Path of the data file in csv format
   
   optional arguments:
     -h, --help            show this help message and exit
     -tc TARGET_COLUMN, --target_column TARGET_COLUMN
                           Name of the column containing the target variable
     -ic [ID_COLUMNS [ID_COLUMNS ...]], --id_columns [ID_COLUMNS [ID_COLUMNS ...]]
                           Name/s of the columns containing the the IDs
     -mdc MEASUREMENT_DATE_COLUMN, --measurement_date_column MEASUREMENT_DATE_COLUMN
                           Name of the column containing the measurement date
     -adc ANCHOR_DATE_COLUMN, --anchor_date_column ANCHOR_DATE_COLUMN
                           Name of the anchor date column
     -wb WINDOW_BEFORE, --window_before WINDOW_BEFORE
                           Number of days or data to include before time-zero. By default: [window_before=0]
     -wa WINDOW_AFTER, --window_after WINDOW_AFTER
                           Number of days or data to include after time-zero. By default: [window_after=3]
     -sp SAVE_PATH, --save_path SAVE_PATH
                           File path to save the results

To Evaluate
~~~~~~~~~~~

To Evaluate the mortality prediction model for a specific data file.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.Evaluate <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -sp <path/to/save/output.json>

Output

A JSON file containing the performance metricies including Fit Time, Score Time, Accuracy, Balanced Accuracy, Average Precision, F1, ROC AUC, and MCCF1 scores.

Build
-----

Predict
-------

EHR2LOS
+++++++


Generic Prediction Utility
++++++++++++++++++++++++++


Set-up Optimisation
+++++++++++++++++++


Time-Window Analysis
--------------------

Sample-Size Analysis
--------------------

Standardisation Analysis
--------------------

Class-Ratio Analysis
--------------------

