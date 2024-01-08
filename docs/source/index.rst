EHR-ML
======

EHR-ML is a comprehensive utility for predictive modelling using the EHR.

It offers 4 different analysis to determine the optimal set-up for modelling a certain clinical outcome, namely;

1. Time-Window Analysis
2. Sample-Size Analysis
3. Standardisation Analysis
4. Class-Ratio Analysis

Additionally, it offers utilities for predicting two clinical outcomes;

1. EHR2Mortality
2. EHR2LOS

Also, there is a generic utility which can be configured to perform any outcome prediction using the EHR.

This utility is primarily designed to handle introcacies of the time-varying signals present in the healthcare data by offering a custom built model for this task.

A command line interface is designed to provide an abstraction over the internal implementation details while at the same time being easy to use for anyone with basic Linux skills. There is also an easy to use web-portal offering all the functionalities of the command-line library.

.. image:: images/ehr_ml_methods.png

.. note::

   This project is under active development.

.. topic:: Acknowledgements

   .. image:: images/monash.png
      :width: 20 %

   .. image:: images/alfred.png
      :width: 20 %

   .. image:: images/superbugai.png
      :width: 20 %

   .. image:: images/RMIT_University_Logo.png
      :width: 20 %

Contents
--------

.. toctree::
   :maxdepth: 1

   install
