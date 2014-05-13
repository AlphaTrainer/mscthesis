.. _appendix_experiment:

================================
 Experiment - signal processing
================================


Run analysis
============


Download code
-------------

Download code from (clone or zip): `<https://github.com/AlphaTrainer/alpha_bci_experiment/tree/final_handin>`_



Prerequests
-----------

Octave 3.6.4 and up [#foot-appendix-octave-download]_.


Load and run
------------

::

    $ cd alpha_bci_experiment
    # load signal processing package of Octave 
    octave> libs_install_and_load
    ...
      class opts;
      ^~~~~
      struct
    1 warning generated.

Just ignore the warning for now we have loaded the signal package successfully
and are ready to run the analysis - do:

::

    octave> run_analysis
    number_of_files =  24
    mindwave/1-20130814-pelle-2-open.mat
    OPEN EYES FIRST
    Discarded bins:0
    Discarded bins:0
    alpha_peak_start_sample =  19
    alpha_peak_end_sample =  23
    ...
    ...

Coffee break while the whole data of the experiment gets processed and
analyzed - at the end we get the result that is added to Table |nbsp|
:num:`table-experiment-final-result-mean`.







.. rubric:: Footnotes

.. [#foot-appendix-octave-download] `<http://www.gnu.org/software/octave/download.html>`_
