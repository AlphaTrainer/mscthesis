.. _appendix_software:

==========
 Software
==========


.. _appendix-alphatrainer-signal-processing-library:

AlphaTrainer signal processing library
======================================

Download code from (clone or zip): `<https://github.com/AlphaTrainer/opencvbrain/tree/finalhandin>`_


Prerequests
-----------

CMake [#foot-appendix-cmake]_ and OpenCV [#foot-appendix-open-cv]_.


Load and run
------------

::

    $ cd opencvbrain/opencvbrain/build
    $ cmake ..
    $ make
    # run the main_brain.cpp of library
    $./opencvbrain
    -- The C compiler identification is Clang 4.2.0
    ...
    [100%] Built target opencvbrain
    ---------------------------------
    getBrainProcessed(...): 6.22933e-17
    expected: 6.22933e-17
    ---------------------------------
    getAlphaPeak(): 10
    expected: 10
    ---------------------------------
    getMinMax(): 0 - 1.03917e+13
    expected: 0 - 1.03917e+13
    ---------------------------------


.. _appendix-alphatrainer-android-app:

AlphaTrainer Android App
========================

Download code from (clone or zip): 

`<https://github.com/AlphaTrainer/AlphaTrainerAndroid/tree/finalhandin>`_


Quick
-----

Simply install the AlphaTrainerApp-debug.apk

::

    $ wget https://github.com/AlphaTrainer/AlphaTrainerAndroid/raw/finalhandin/AlphaTrainerApp-debug.apk
    $ adb install <path-to-apk>/AlphaTrainerApp-debug.apk



Build from scratch
------------------


** Prerequests **


We assume all Android tools (ADT) like adb, NDK [#foot-appendix-android-ndk]_, etc are setup.

OpenCV Android SDK 2.4.6 [#foot-appendix-open-cv-android-sdk]_ and have it set
in the build path:

::

    $ ls $OPENCV_ANDROID_SDK
    etc	java	native


** Use the shell scripts **

::

    $ cd <some dir that have a check out of opencvbrain>
    $ ls 
    AlphaTrainerAndroid	opencvbrain 
    ...
    $ cd AlphaTrainerAndroid
    # step 0: build native lib stand alone 
    $ build_0_opencvbrain.sh
    ...
    # step 1: build native lib into app with ndk
    $ build_1_ndk_brainapp.sh
    # step 2 build and install android app:
    $ build_2_android_brainapp.sh




.. _appendix-alphatrainer-service:

AlphaTrainerService
===================

Runs at MongoLab [#foot-appendix-mongolab]_ and Heroku [#foot-appendix-heroku]_: `<http://alpha-trainer.herokuapp.com/>`_.

.. _appendix-alphatrainer-mongolab-cloud-storage:

Mongolab cloud storage
----------------------

Using the the version 2 beta we can for example query all feedback trainings and ignore the *alpha_levels*:

::

    GET https://data-api.mongolab.com/v2/apis/dk5jpmcf2g1bg/collections/trainings
    /documents?fields=%7B%22alpha_levels%22%3A0%7D&query=%7B%22type%22%3A%22Feedback%22%7D</code>
    
Last part not url encoded:

::

    /documents?q={"type":"Feedback"}&fields={"alpha_levels":0}</code>

Reference the full API at `<http://alpha-trainer.herokuapp.com/>`_.


.. _appendix-alphatrainerservice-client:

AlphaTrainerService client
--------------------------

Download code from (clone or zip): 

`<https://github.com/AlphaTrainer/AlphaTrainerService/tree/finalhandin>`_

Download the *Typesafe Activator* a tool on top of the *Play Framework*
[#foot-appendix-playframework-activator]_. Ensure to have *Activator* in your
build path:

::

    $ which activator
    <path to>/activator-1.0.0/activator

OK then start it:

::

    $ cd <path to>/AlphaTrainerService
    $ ./activator run 
    # listen to file changes use
    $ ./activator ~run 

And then open the client in a browser.


.. rubric:: Footnotes

.. [#foot-appendix-open-cv] `<http://opencv.org>`_

.. [#foot-appendix-cmake] `<http://www.cmake.org>`_.

.. [#foot-appendix-android-ndk] `<http://developer.android.com/tools/sdk/ndk/index.html>`_

.. [#foot-appendix-open-cv-android-sdk] `<http://opencv.org/downloads.html>`_

.. [#foot-appendix-playframework-activator] `<http://www.playframework.com/download>`_

.. [#foot-appendix-mongolab] `<https://mongolab.com>`_

.. [#foot-appendix-heroku] `<https://www.heroku.com>`_
