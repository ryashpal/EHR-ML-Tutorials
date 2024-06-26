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

    (.venv) app_user@hostname:~$python -m ehrml.ehr2mortality.Evaluate <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -sp <path/to/save/metrics.json>

Output

A JSON file containing the performance metricies including Fit Time, Score Time, Accuracy, Balanced Accuracy, Average Precision, F1, ROC AUC, and MCCF1 scores.

Build
-----

This utility will help to build a mortality prediction model using the parameters specified.

Help menu
~~~~~~~~~

To display the help menu of the Build functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2mortality.Build -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2mortality.Build --help


Output

.. code-block:: console

   usage: Build.py [-h] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-tc TARGET_COLUMN] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN] [-wb WINDOW_BEFORE] [-wa WINDOW_AFTER]
                   [-sp SAVE_PATH]
                   data_file
   
   EHR-ML machine learning utility
   
   positional arguments:
     data_file             Path of the data file in csv format
   
   optional arguments:
     -h, --help            show this help message and exit
     -ic [ID_COLUMNS [ID_COLUMNS ...]], --id_columns [ID_COLUMNS [ID_COLUMNS ...]]
                           Name/s of the columns containing the the IDs
     -tc TARGET_COLUMN, --target_column TARGET_COLUMN
                           Name of the column containing the target variable
     -mdc MEASUREMENT_DATE_COLUMN, --measurement_date_column MEASUREMENT_DATE_COLUMN
                           Name of the column containing the measurement date
     -adc ANCHOR_DATE_COLUMN, --anchor_date_column ANCHOR_DATE_COLUMN
                           Name of the anchor date column
     -wb WINDOW_BEFORE, --window_before WINDOW_BEFORE
                           Number of days or data to include before time-zero. By default: [window_before=0]
     -wa WINDOW_AFTER, --window_after WINDOW_AFTER
                           Number of days or data to include after time-zero. By default: [window_after=3]
     -sp SAVE_PATH, --save_path SAVE_PATH
                           File path to save the model

To Build
~~~~~~~~

To Build the mortality prediction model for a specific data file.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2mortality.Evaluate <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -sp <path/to/save/model.pkl>

Output

A pickle file containing a built model.


Predict
-------

This utility will help to perform predictions using the mortality prediction model.

Help menu
~~~~~~~~~

To display the help menu of the Predict functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2mortality.Predict -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2mortality.Predict --help


Output

.. code-block:: console

   usage: Predict.py [-h] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-tc TARGET_COLUMN] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN] [-wb WINDOW_BEFORE] [-wa WINDOW_AFTER]
                     [-mp MODEL_PATH] [-sp SAVE_PATH]
                     data_file
   
   EHR-ML machine learning utility
   
   positional arguments:
     data_file             Path of the data file in csv format
   
   optional arguments:
     -h, --help            show this help message and exit
     -ic [ID_COLUMNS [ID_COLUMNS ...]], --id_columns [ID_COLUMNS [ID_COLUMNS ...]]
                           Name/s of the columns containing the the IDs
     -tc TARGET_COLUMN, --target_column TARGET_COLUMN
                           Name of the column containing the target variable
     -mdc MEASUREMENT_DATE_COLUMN, --measurement_date_column MEASUREMENT_DATE_COLUMN
                           Name of the column containing the measurement date
     -adc ANCHOR_DATE_COLUMN, --anchor_date_column ANCHOR_DATE_COLUMN
                           Name of the anchor date column
     -wb WINDOW_BEFORE, --window_before WINDOW_BEFORE
                           Number of days or data to include before time-zero. By default: [window_before=0]
     -wa WINDOW_AFTER, --window_after WINDOW_AFTER
                           Number of days or data to include after time-zero. By default: [window_after=3]
     -mp MODEL_PATH, --model_path MODEL_PATH
                           File containing the model
     -sp SAVE_PATH, --save_path SAVE_PATH
                           File path to save the model predictions

To Predict
~~~~~~~~~~

To perform predictions using the mortality prediction model.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2mortality.Evaluate <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -mp <path/to/save/model.pkl> -sp <path/to/save/predictions.csv>

Output

A csv file containing the predictions.


EHR2LOS
+++++++

Evaluate
--------

This utility will help to evaluate the performance of LOS prediction model using 5-fold cross validation.

Help menu
~~~~~~~~~

To display the help menu of the Evaluate functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2los.Evaluate -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2los.Evaluate --help


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

To Evaluate the LOS prediction model for a specific data file.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2los.Evaluate <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -sp <path/to/save/metrics.json>

Output

A JSON file containing the performance metricies including Fit Time, Score Time, Accuracy, Balanced Accuracy, Average Precision, F1, ROC AUC, and MCCF1 scores.

Build
-----

This utility will help to build a LOS prediction model using the parameters specified.

Help menu
~~~~~~~~~

To display the help menu of the Build functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2los.Build -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2los.Build --help


Output

.. code-block:: console

   usage: Build.py [-h] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-tc TARGET_COLUMN] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN] [-wb WINDOW_BEFORE] [-wa WINDOW_AFTER]
                   [-sp SAVE_PATH]
                   data_file
   
   EHR-ML machine learning utility
   
   positional arguments:
     data_file             Path of the data file in csv format
   
   optional arguments:
     -h, --help            show this help message and exit
     -ic [ID_COLUMNS [ID_COLUMNS ...]], --id_columns [ID_COLUMNS [ID_COLUMNS ...]]
                           Name/s of the columns containing the the IDs
     -tc TARGET_COLUMN, --target_column TARGET_COLUMN
                           Name of the column containing the target variable
     -mdc MEASUREMENT_DATE_COLUMN, --measurement_date_column MEASUREMENT_DATE_COLUMN
                           Name of the column containing the measurement date
     -adc ANCHOR_DATE_COLUMN, --anchor_date_column ANCHOR_DATE_COLUMN
                           Name of the anchor date column
     -wb WINDOW_BEFORE, --window_before WINDOW_BEFORE
                           Number of days or data to include before time-zero. By default: [window_before=0]
     -wa WINDOW_AFTER, --window_after WINDOW_AFTER
                           Number of days or data to include after time-zero. By default: [window_after=3]
     -sp SAVE_PATH, --save_path SAVE_PATH
                           File path to save the model

To Build
~~~~~~~~

To Build the LOS prediction model for a specific data file.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2los.Evaluate <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -sp <path/to/save/model.pkl>

Output

A pickle file containing a built model.


Predict
-------

This utility will help to perform predictions using the mortality prediction model.

Help menu
~~~~~~~~~

To display the help menu of the Predict functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2los.Predict -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2los.Predict --help


Output

.. code-block:: console

   usage: Predict.py [-h] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-tc TARGET_COLUMN] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN] [-wb WINDOW_BEFORE] [-wa WINDOW_AFTER]
                     [-mp MODEL_PATH] [-sp SAVE_PATH]
                     data_file
   
   EHR-ML machine learning utility
   
   positional arguments:
     data_file             Path of the data file in csv format
   
   optional arguments:
     -h, --help            show this help message and exit
     -ic [ID_COLUMNS [ID_COLUMNS ...]], --id_columns [ID_COLUMNS [ID_COLUMNS ...]]
                           Name/s of the columns containing the the IDs
     -tc TARGET_COLUMN, --target_column TARGET_COLUMN
                           Name of the column containing the target variable
     -mdc MEASUREMENT_DATE_COLUMN, --measurement_date_column MEASUREMENT_DATE_COLUMN
                           Name of the column containing the measurement date
     -adc ANCHOR_DATE_COLUMN, --anchor_date_column ANCHOR_DATE_COLUMN
                           Name of the anchor date column
     -wb WINDOW_BEFORE, --window_before WINDOW_BEFORE
                           Number of days or data to include before time-zero. By default: [window_before=0]
     -wa WINDOW_AFTER, --window_after WINDOW_AFTER
                           Number of days or data to include after time-zero. By default: [window_after=3]
     -mp MODEL_PATH, --model_path MODEL_PATH
                           File containing the model
     -sp SAVE_PATH, --save_path SAVE_PATH
                           File path to save the model predictions

To Predict
~~~~~~~~~~

To perform predictions using the mortality prediction model.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ehr2los.Evaluate <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -mp <path/to/save/model.pkl> -sp <path/to/save/predictions.csv>

Output

A csv file containing the predictions.


Generic Prediction Utility
++++++++++++++++++++++++++

Evaluate
--------

This utility will help to evaluate the performance of a generic prediction model using 5-fold cross validation.

Help menu
~~~~~~~~~

To display the help menu of the Evaluate functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.Evaluate -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.Evaluate --help


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

To Evaluate the generic prediction model for a specific data file.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.Evaluate <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -sp <path/to/save/metrics.json>

Output

A JSON file containing the performance metricies including Fit Time, Score Time, Accuracy, Balanced Accuracy, Average Precision, F1, ROC AUC, and MCCF1 scores.

Build
-----

This utility will help to build a generic prediction model using the parameters specified.

Help menu
~~~~~~~~~

To display the help menu of the Build functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.Build -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.Build --help


Output

.. code-block:: console

   usage: Build.py [-h] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-tc TARGET_COLUMN] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN] [-wb WINDOW_BEFORE] [-wa WINDOW_AFTER]
                   [-sp SAVE_PATH]
                   data_file
   
   EHR-ML machine learning utility
   
   positional arguments:
     data_file             Path of the data file in csv format
   
   optional arguments:
     -h, --help            show this help message and exit
     -ic [ID_COLUMNS [ID_COLUMNS ...]], --id_columns [ID_COLUMNS [ID_COLUMNS ...]]
                           Name/s of the columns containing the the IDs
     -tc TARGET_COLUMN, --target_column TARGET_COLUMN
                           Name of the column containing the target variable
     -mdc MEASUREMENT_DATE_COLUMN, --measurement_date_column MEASUREMENT_DATE_COLUMN
                           Name of the column containing the measurement date
     -adc ANCHOR_DATE_COLUMN, --anchor_date_column ANCHOR_DATE_COLUMN
                           Name of the anchor date column
     -wb WINDOW_BEFORE, --window_before WINDOW_BEFORE
                           Number of days or data to include before time-zero. By default: [window_before=0]
     -wa WINDOW_AFTER, --window_after WINDOW_AFTER
                           Number of days or data to include after time-zero. By default: [window_after=3]
     -sp SAVE_PATH, --save_path SAVE_PATH
                           File path to save the model

To Build
~~~~~~~~

To Build the generic prediction model for a specific data file.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.Evaluate <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -sp <path/to/save/model.pkl>

Output

A pickle file containing a built model.


Predict
-------

This utility will help to perform predictions using the generic prediction model.

Help menu
~~~~~~~~~

To display the help menu of the Predict functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.Predict -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.Predict --help


Output

.. code-block:: console

   usage: Predict.py [-h] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-tc TARGET_COLUMN] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN] [-wb WINDOW_BEFORE] [-wa WINDOW_AFTER]
                     [-mp MODEL_PATH] [-sp SAVE_PATH]
                     data_file
   
   EHR-ML machine learning utility
   
   positional arguments:
     data_file             Path of the data file in csv format
   
   optional arguments:
     -h, --help            show this help message and exit
     -ic [ID_COLUMNS [ID_COLUMNS ...]], --id_columns [ID_COLUMNS [ID_COLUMNS ...]]
                           Name/s of the columns containing the the IDs
     -tc TARGET_COLUMN, --target_column TARGET_COLUMN
                           Name of the column containing the target variable
     -mdc MEASUREMENT_DATE_COLUMN, --measurement_date_column MEASUREMENT_DATE_COLUMN
                           Name of the column containing the measurement date
     -adc ANCHOR_DATE_COLUMN, --anchor_date_column ANCHOR_DATE_COLUMN
                           Name of the anchor date column
     -wb WINDOW_BEFORE, --window_before WINDOW_BEFORE
                           Number of days or data to include before time-zero. By default: [window_before=0]
     -wa WINDOW_AFTER, --window_after WINDOW_AFTER
                           Number of days or data to include after time-zero. By default: [window_after=3]
     -mp MODEL_PATH, --model_path MODEL_PATH
                           File containing the model
     -sp SAVE_PATH, --save_path SAVE_PATH
                           File path to save the model predictions

To Predict
~~~~~~~~~~

To perform predictions using the mortality prediction model.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.Evaluate <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -mp <path/to/save/model.pkl> -sp <path/to/save/predictions.csv>

Output

A csv file containing the predictions.

Feature Importance
------------------

This utility will help to obtain the feature importance measures of the built ensemble models.

Help menu
~~~~~~~~~

To display the help menu of the Feature Importance functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.FeatureImportance -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.FeatureImportance --help


Output

.. code-block:: console

   usage: FeatureImportance.py [-h] [-i] [-sp SAVE_PATH] model_file
   
   EHR-ML machine learning utility
   
   positional arguments:
     model_file            Path of the ensemble model file in pkl format
   
   options:
     -h, --help            show this help message and exit
     -i, --intermediate    Include feature importance of intermediate features
     -p, --plot            Plot the important features
     -f FEATURES, --features FEATURES
                        Number of features to plot (required only with the -p option). By default: [features=10]
     -sp SAVE_PATH, --save_path SAVE_PATH
                           File path to save the feature importance


To obtain Feature Importance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To obtain the feature importance for a built ensemble model.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble.FeatureImportance <path/to/model.pkl> -i <optional: to get the intermediate features> -p <optional: to plot the important features> -f <required only with -p: number of features to plot> -sp <path/to/save/output/files/>

Output

A csv file containing the predictions and optionally a plot showing top n features, both saved in the specified savepath.


Time-Series Data Splitting
--------------------------

This utility will split the time series data in chronological order. This enables the creation of training sets using past episodes from a point of reference and future testing sets containing information that is temporally disconnected to the training data.

Help menu
~~~~~~~~~

To display the help menu of the Time-Series Data Splitting functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.split.TimeSeries -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.split.TimeSeries --help


Output

.. code-block:: console

   usage: TimeSeries.py [-h] [-s N_SPLITS] [-g GAP] [-sp SAVE_PATH] data_file
   
   EHR-ML machine learning utility
   
   positional arguments:
     data_file             Path of the data file in csv format
   
   optional arguments:
     -h, --help            show this help message and exit
     -s N_SPLITS, --n_splits N_SPLITS
                           Number of splits to perform. By default: [n_splits=5]
     -g GAP, --gap GAP     Gap between the training and test set. By default: [gap=0]
     -sp SAVE_PATH, --save_path SAVE_PATH
                           Path to save the splits


To perform time series split
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To perform the time series split for a give data.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.split.TimeSeries <path/to/data.csv> -s <Number of splits to perform> -g <Gap between the training and test set> -sp <path/to/save/splitted/files/>

Output

Train and test csv files containing the splitted data, saved in the specified savepath.


Generic Prediction Utility - V2
+++++++++++++++++++++++++++++++

Build
-----

This utility will help to build a generic ensemble model using the parameters specified in the command line arguments and the configuration file.

Help menu
~~~~~~~~~

To display the help menu of the Build functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble_v2.Build -h

or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble_v2.Build --help


Output

.. code-block:: console

   usage: Build.py [-h] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-tc TARGET_COLUMN] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN] [-wb WINDOW_BEFORE] [-wa WINDOW_AFTER]
                   [-sp SAVE_PATH]
                   data_file
   
   EHR-ML machine learning utility
   
   positional arguments:
     data_file             Path of the data file in csv format
   
   optional arguments:
     -h, --help            show this help message and exit
     -ic [ID_COLUMNS [ID_COLUMNS ...]], --id_columns [ID_COLUMNS [ID_COLUMNS ...]]
                           Name/s of the columns containing the the IDs
     -tc TARGET_COLUMN, --target_column TARGET_COLUMN
                           Name of the column containing the target variable
     -mdc MEASUREMENT_DATE_COLUMN, --measurement_date_column MEASUREMENT_DATE_COLUMN
                           Name of the column containing the measurement date
     -adc ANCHOR_DATE_COLUMN, --anchor_date_column ANCHOR_DATE_COLUMN
                           Name of the anchor date column
     -wb WINDOW_BEFORE, --window_before WINDOW_BEFORE
                           Number of days or data to include before time-zero. By default: [window_before=0]
     -wa WINDOW_AFTER, --window_after WINDOW_AFTER
                           Number of days or data to include after time-zero. By default: [window_after=3]
     -cf CONFIG_FILE, --config_file CONFIG_FILE
                        Configuration module
     -sp SAVE_PATH, --save_path SAVE_PATH
                           File path to save the model

To Build
~~~~~~~~

To Build the generic prediction model for a specific data file.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble_v2.Build <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -cf <path/to/config/module> -sp <path/to/save/model.pkl>

Output

A pickle file containing a built ensemble model as specified in the configuration file.

Configuration
~~~~~~~~~~~~~

The configuration files allows the flexibility to define the internal constituent models used to build the ensemble model. Addtitionally, it allows to specify the search range to be employed for the hyperparameter tuning. Essentially, this feature allows to custom design the ensemble structure and the tuning range of hyperparameters while building an ensemble model.

The configuration contains the following tags;

.. code-block:: json

    # Execute block structure
    'model_name': {
        'model': <function to get the classifier>,
        'search_params' : [
        {'parameter_1' : <search range 1>},
        {'parameter_2' : <search range 2>},
            ...
            ...
        {'parameter_3' : <search range 3>},
        ]
    },

Please refer the table below for information on the configuration fields.

+----------------------+-----------------------------------------------------------------------------+
| Configuration Field  | Field Details                                                               |
+----------------------+-----------------------------------------------------------------------------+
| model_name           | Identification name given to an internal constituent model                  |
+----------------------+-----------------------------------------------------------------------------+
| model                | A fucntion that returns the model by importing from any external library    |
+----------------------+-----------------------------------------------------------------------------+
| search_params        | a list of search parameter and their value ranges for hyperparameter tuning |
+----------------------+-----------------------------------------------------------------------------+

An example configuration block for including ``Logistic Regression Classifier`` in the ensemble is given below;

.. code-block:: json

   # Execute block structure
    'lr': {
        'model': getLogisticRegression,
        'search_params' : [
            {'solver': ['newton-cg', 'liblinear']},
            {'C': [1000, 100, 10, 1.0, 0.1, 0.01]},
        ]
    },


.. note::

   This configuration allows the flexibility to use any machine learning model imported from third party libraries in the ensemble structure. The function specified in the ``model`` parameter should import the necessary libraries and define any static configurations if necessary before returning the model.

Predict
-------

This utility will help to perform predictions using the ensemble model.

Help menu
~~~~~~~~~

To display the help menu of the Predict functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble_v2.Predict -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble_v2.Predict --help


Output

.. code-block:: console

   usage: Predict.py [-h] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-tc TARGET_COLUMN] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN] [-wb WINDOW_BEFORE] [-wa WINDOW_AFTER]
                     [-mp MODEL_PATH] [-sp SAVE_PATH]
                     data_file
   
   EHR-ML machine learning utility
   
   positional arguments:
     data_file             Path of the data file in csv format
   
   optional arguments:
     -h, --help            show this help message and exit
     -ic [ID_COLUMNS [ID_COLUMNS ...]], --id_columns [ID_COLUMNS [ID_COLUMNS ...]]
                           Name/s of the columns containing the the IDs
     -tc TARGET_COLUMN, --target_column TARGET_COLUMN
                           Name of the column containing the target variable
     -mdc MEASUREMENT_DATE_COLUMN, --measurement_date_column MEASUREMENT_DATE_COLUMN
                           Name of the column containing the measurement date
     -adc ANCHOR_DATE_COLUMN, --anchor_date_column ANCHOR_DATE_COLUMN
                           Name of the anchor date column
     -wb WINDOW_BEFORE, --window_before WINDOW_BEFORE
                           Number of days or data to include before time-zero. By default: [window_before=0]
     -wa WINDOW_AFTER, --window_after WINDOW_AFTER
                           Number of days or data to include after time-zero. By default: [window_after=3]
     -mp MODEL_PATH, --model_path MODEL_PATH
                           File containing the model
     -sp SAVE_PATH, --save_path SAVE_PATH
                           File path to save the model predictions

To Predict
~~~~~~~~~~

To perform predictions using the mortality prediction model.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.ensemble_v2.Evaluate <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -mp <path/to/save/model.pkl> -sp <path/to/save/predictions.csv>

Output

A csv file containing the predictions.


Set-up Optimisation (Benchmarking)
++++++++++++++++++++++++++++++++++

This section deals with determining the best set-up for modelling clinical outcomes.

Time-Window Analysis
--------------------

This utility will help to understand the effect of time-window on the predictive performance.

Help menu
~~~~~~~~~

To display the help menu of the time-window analysis functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.analysis.TimeWindowAnalysis -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.analysis.TimeWindowAnalysis --help


Output

.. code-block:: console

   usage: TimeWindowAnalysis.py [-h] [-tc TARGET_COLUMN] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN]
                                [-wb [WINDOW_BEFORE_LIST [WINDOW_BEFORE_LIST ...]]] [-wa [WINDOW_AFTER_LIST [WINDOW_AFTER_LIST ...]]] [-e] [-sp SAVE_PATH]
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
     -wb [WINDOW_BEFORE_LIST [WINDOW_BEFORE_LIST ...]], --window_before_list [WINDOW_BEFORE_LIST [WINDOW_BEFORE_LIST ...]]
                           Number of days or data to include before time-zero.
     -wa [WINDOW_AFTER_LIST [WINDOW_AFTER_LIST ...]], --window_after_list [WINDOW_AFTER_LIST [WINDOW_AFTER_LIST ...]]
                           Number of days or data to include after time-zero.
     -e, --ensemble        Use ensemble model.
     -sp SAVE_PATH, --save_path SAVE_PATH
                           Directory path to save the results and intermediate files

Analyse
~~~~~~~

To perform time-window analysis for a combination of specified window start and end boundary values. For instance, if the -wb is [0, 1] and -wa is [1, 2, 3], the analysis will be performed for the windows [(0, 1), (0, 2), (0, 3), (1, 1), (1, 2), (1, 3)].

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.analysis.TimeWindowAnalysis <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before Value List> -wa <Window After Value List> -e -sp <path/to/save/predictions.csv>

.. note::

    You have the flexibility to run this analysis with either a standalone or ensemble model, easily enabled by the -e switch.

Output

Multiple csv files containing the predictions saved at the specified path each corresponding to the supplied data windows.


Sample-Size Analysis
--------------------

This utility will help to understand the effect of sample-size on the predictive performance.

Help menu
~~~~~~~~~

To display the help menu of the sample-size analysis functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.analysis.SampleSizeAnalysis -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.analysis.SampleSizeAnalysis --help


Output

.. code-block:: console

   usage: SampleSizeAnalysis.py [-h] [-tc TARGET_COLUMN] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN] [-wb WINDOW_BEFORE]
                                [-wa WINDOW_AFTER] [-ss [SAMPLE_SIZE [SAMPLE_SIZE ...]]] [-e] [-sp SAVE_PATH]
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
     -ss [SAMPLE_SIZE [SAMPLE_SIZE ...]], --sample_size [SAMPLE_SIZE [SAMPLE_SIZE ...]]
                           Sample Sizes
     -e, --ensemble        Use ensemble model.
     -sp SAVE_PATH, --save_path SAVE_PATH
                           Directory path to save the results and intermediate files

Analyse
~~~~~~~

To perform sample-size analysis for a series of specified sample size values.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.analysis.SampleSizeAnalysis <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -ss <List of Sample Sizes> -e -sp <path/to/save/predictions.csv>

.. note::

    You have the flexibility to run this analysis with either a standalone or ensemble model, easily enabled by the -e switch.

Output

Multiple csv files containing the predictions saved at the specified path each corresponding to the supplied sample sizes.


Standardisation Analysis
------------------------

This utility will help to understand the effect of standardisation on the predictive performance.

Help menu
~~~~~~~~~

To display the help menu of the standardisation analysis functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.analysis.StandardisationAnalysis -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.analysis.StandardisationAnalysis --help


Output

.. code-block:: console

   usage: StandardisationAnalysis.py [-h] [-tc TARGET_COLUMN] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN] [-wb WINDOW_BEFORE]
                                     [-wa WINDOW_AFTER] [-e] [-sp SAVE_DIR]
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
     -e, --ensemble        Use ensemble model.
     -sp SAVE_DIR, --save_dir SAVE_DIR
                           Directory to save the results and intermediate files

Analyse
~~~~~~~

To perform standardisation analysis comparing the raw data, standard-scaled data, and the min-max-scaled data.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.analysis.StandardisationAnalysis <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -e -sp <path/to/save/predictions.csv>

.. note::

    You have the flexibility to run this analysis with either a standalone or ensemble model, easily enabled by the -e switch.

Output

Multiple csv files containing the predictions saved at the specified path each corresponding to the raw data, standard-scaled data, and the min-max-scaled data.

Class-Ratio Analysis
--------------------

This utility will help to understand the effect of class-ratio on the predictive performance.

Help menu
~~~~~~~~~

To display the help menu of the class-ratio analysis functionality.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.analysis.ClassRatioAnalysis -h


or

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.analysis.ClassRatioAnalysis --help


Output

.. code-block:: console

   usage: ClassRatioAnalysis.py [-h] [-tc TARGET_COLUMN] [-ic [ID_COLUMNS [ID_COLUMNS ...]]] [-mdc MEASUREMENT_DATE_COLUMN] [-adc ANCHOR_DATE_COLUMN] [-wb WINDOW_BEFORE]
                                [-wa WINDOW_AFTER] [-pcp [POSITIVE_CLASS_PROPORTIONS [POSITIVE_CLASS_PROPORTIONS ...]]] [-e] [-sp SAVE_PATH]
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
     -pcp [POSITIVE_CLASS_PROPORTIONS [POSITIVE_CLASS_PROPORTIONS ...]], --positive_class_proportions [POSITIVE_CLASS_PROPORTIONS [POSITIVE_CLASS_PROPORTIONS ...]]
                           Positive Class Proportions
     -e, --ensemble        Use ensemble model.
     -sp SAVE_PATH, --save_path SAVE_PATH
                           Directory path to save the results and intermediate files

Analyse
~~~~~~~

To perform class-ratio analysis for a series of specified class ratio values. For every positive class proportion (pcp) specified, the corresponding negative class proportion (ncp) is calculated by the formula ncp = 100 - pcp. For instance, if the positive class proportion is pcp = 40, then the corresponding negative class proportion is obtained by ncp = 100-40 which is 60. Next, for every value in the specified pcp, the negative class is downsampled to create the specified ratio for running this analysis.

.. code-block:: console

    (.venv) app_user@hostname:~$python -m ehrml.analysis.ClassRatioAnalysis <path/to/input/data.csv> -tc <Target Column Name> -ic <ID Column 1> <ID Column 2> -mdc <Measurement Data Column> -adc <Anchor Data Column> -wb <Window Before> -wa <Window After> -pcp <List of Positive Class Proportions> -e -sp <path/to/save/predictions.csv>

.. note::

    You have the flexibility to run this analysis with either a standalone or ensemble model, easily enabled by the -e switch.

Output

Multiple csv files containing the predictions saved at the specified path each corresponding to the supplied class ratios.


