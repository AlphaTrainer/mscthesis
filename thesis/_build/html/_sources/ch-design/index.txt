.. _ch-design:

========
 Design
========

So far, this thesis has established some important notions that we use as input
to the design of AlphaTrainer: (*i*) from the Background Chapter |nbsp|
:ref:`ch-background` we learned that alpha feedback training can benefit to
reduce stress; (*ii*) from the BCI Evaluation Chapter |nbsp|
:ref:`ch-experiment` we learned that the MindWave Mobile BCI is feasible for
building an alpha feedback training system; and (*iii*) in the Introduction
Chapter |nbsp| :ref:`ch-intro` we presented our overall method which includes
the need for a robust system deployable for real world use.

These three notions span the design space for building AlphaTrainer. This
chapter first describes the design model and method used and then moves on to
explain some of the important design activities and choices made during the
design process and finally present the design of AlphaTrainer.


.. _ch-design-model-and-method:

Design model and method
=======================

This section presents the model used throughout the design of AlphaTrainer and
the set of methods used during the design process. We start out by placing the
design problem at hand within a Human-Computer Interaction (HCI) context which
motivates the choice of design model.

The ISO 9241-210:2010 standard for "Human-centred design for interactive
systems" states the following about HCI design:

"*The complexity of human-computer interaction means that it is impossible to
specify completely and accurately every detail of every aspect of the
interaction at the beginning of development. Many of the needs and expectations
of users and other stakeholders only emerge [...] as the designers refine their
understanding of users and their tasks, and as users are better able to express
their needs in response to potential solutions*" |nbsp| :cite:p:`iso_iso_2010`
Section 4.5 p. 6.

Since we are designing a system which aims to enable a currently non-existing
practice - namely to perform alpha feedback training on a mobile device in an
everyday context - we are certainly struck by the complexity in regard to
specifying user needs up-front.

When designing for ubicomp, additional aspects has to be taken in consideration
which further increase complexity: (*i*) different devices; (*ii*) mobile users;
and (*iii*) changing environment and context |nbsp|
:cite:p:`bardram_ubiquitous_2010`. We recognize that we are not only designing
interfaces but also designing interactions between people and the system through
some artifacts embedded in an environment |nbsp|
:cite:p:`beaudouin-lafon_designing_2004`. In a neurofeedback training system we
have: (*i*) a user; (*ii*) using artifacts in form of the mobile device and the
headset; and (*iii*) in an environment with a lot of parameters such as noise,
changing lights, other people etc. This requires us to think of the interaction
in context - *in-situ* - at home, at work or somewhere in between (e.g. when
commuting) |nbsp| :cite:p:`benyon_designing_2005` |nbsp|
:cite:p:`abowd_human_2002`.

To deal with the complexity and difficulty of specifying user needs and system
requirements up front, we take a user centered approach to our design
process. This approach enables specifications to emerge during the design
process through experiments and prototypes from which we will learn and design
new experiments and prototypes |nbsp| :cite:p:`benyon_designing_2005` |nbsp|
:cite:p:`klemmer_how_2006`. We have drawn the model in Figure |nbsp|
:num:`fig-iterative-model`.


.. _fig-iterative-model:

.. figure:: fig/theiterativemodel.png
    :alt: The iterative model.
    :width: 60%
    :align: center
    
    The iterative model.


To envision the needs and goals of the users of our system we have been using
personas and scenarios |nbsp| :cite:p:`kollmann_importance_2009`
:cite:p:`benyon_designing_2010`. A persona simply model a certain user in order
to delimit the target group for whom we are designing AlphaTrainer. We have
created four personas named Morten, Niels, Olivia and Peter (Appendix |nbsp|
:ref:`appendix_design_personas`). We are using scenarios to frame the context
and situation when and where the system is used. As a subset of scenarios we
have worked with some simple storyboards to capture the setting, sequence and
satisfaction of the actual alpha training (Appendix |nbsp|
:ref:`appendix_design_storyboards`).

One of the storyboards cover a work scenario and the person could be *Peter*
(Figure |nbsp| :num:`fig-design-scenario-work`). *Peter* has had a busy day with
a lot of meetings and deadlines waiting around the corner. It is 11.30 and he
realizes that he can squeeze in alpha feedback training just before lunch to get
his mind clear. Peter finds a silent spot in the office space which mostly
consists of big open spaces but luckily there has been arranged some quiet
spots around. He chooses one of the feedbacks with sound because it is
convenient to use when training with earphones in an office environment.
First he does the calibration, then the reference recording as the app
asks for and finally he performs three 5 minutes training sessions in a row. He
improves his alpha during training and finds himself in a relaxed mental state
after the training. Back to work.


.. _fig-design-scenario-work:

.. figure:: fig/design-scenario-work.png
    :alt: Alpha training at work 
    :width: 100%
    :align: center
    
    Peter performing alpha training at work. Frame 1: Peter has a busy day with a lot of deadlines waiting around the corner. Frame 2: Before lunch, he finds a quiet spot. Frame 3: He performs 15 minutes of alpha training. Frame 4: He finds himself relaxed and gets back to work.



.. _ch-design-process:

Design process
==============

Since we have deployed an iterative approach to the design process, we have
decided to present important design activities and decisions
chronologically. This clarifies how we continuously have fed the output of one
design activity as input to another.


Initial experimental prototype
------------------------------

We started out by making a very simple prototype in the form of an Android app
as proof of concept on getting data from the NeuroSky MindWave Mobile BCI and to
tryout of their SDK signal processing. In a bottom up approach to investigate
what we could control by means of alpha levels, we tried assigning different
audio parameters (volume, pitch, placement in 3D perspective) to the SDK power
band values for low and high alpha. The power band values are listed in Section
|nbsp| :ref:`ch-background-mindwave`.


We tried out the prototype informally on our selves and on fellow students and
learned that the SDK alpha values contained giant outliers as already mentioned
in the BCI Evaluation Chapter |nbsp| :ref:`ch-experiment`. Besides, we were
unsure whether to use the low alpha or high alpha frequency band from the SDK
since the literature states - as explained in Section |nbsp|
:ref:`sec-background-stress-alpha-feedback-training` - that the alpha band
varies between individuals and that neurofeedback is significantly more
effective when the feedback is given on individually adapted frequency bands.

In researching how neurofeedback is practiced, we contacted Ann-Helen
Pettersen - one of the few Danish psychiatrists specializing in neurofeedback
therapy |nbsp| [#foot-background-hjernetraening]_.  She also stressed the
importance of accounting for individually determined frequency bands.  When
practicing neurofeedback therapy, she starts out by recording a map of EEG
frequency intensities. This "brain map", as she calls it, serves as input to the
choice of an appropriate feedback frequency band.

Based on the notions from the literature on alpha feedback training backed up by a
clinician's neurofeedback practice, we decided that our alpha training system
would need the ability to give feedback on an alpha band adapted to the
individual alpha peak frequency. This led us to experiment with doing the
frequency analysis our selves. This
also enabled us to test whether we could reproduce the outliers experienced from
the SDK alpha values which would inform about whether they originated from the
raw data or from the SDK processing.

We did the signal processing offline (see Section |nbsp|
:ref:`ch-experiment-pre-study`) and interestingly we were not able to reproduce
the outliers we got from the SDK. Another interesting find during the data
analysis was that the alpha wave intensity comes in chunks of a few seconds
length as can be seen, for example, in Figure |nbsp|
:num:`fig-experiment-final-7-mindwave-alpha-progress`.  The chunks of high alpha
activity can even be observed directly from a raw EEG signal such as the one
shown in Figure |nbsp| :num:`fig-eeg-with-alpha-waves`.


Early functioning Android prototype
-----------------------------------

.. Engineer level prototype
.. - focus on information, what information is given to the user, etc.
.. - abstract away layout, interaction, etc.
.. - hook up MindWave raw data -> native signal processing -> first batch of simple feedbacks: box, box w history, bar, bar w history, growing bar (additive)

As the next step we implemented a working Android alpha feedback training
prototype. We focused on the needs for custom signal processing revealed in our
previous prototype experiments and from the literature. Our approach to signal
processing is covered in the Implementation Chapter |nbsp|
:ref:`ch-implementation`. We also created a set of 5 different feedback views
inspired by other neurofeedback systems.

The views were variations over a bar changing height and a box changing
color. We read about the bar feedback in |nbsp|
:cite:p:`larsen_classification_2011` describing its clinical usage in ADHD
treatment. The goal for the trainee is to raise the bar which in our case
represents the magnitude of alpha waves. The basic bar feedback is shown in
Figure |nbsp| :num:`fig-early-prototype-feedback-bar`. The feedback consisting
of a box changing colors was used in the Smartphone Brain Scanner alpha feedback
training application as mentioned in the Background Chapter |nbsp|
:ref:`ch-background`. In our case, the
box gradually change from red over yellow to green. The trainees goal is to make
and keep the box green which represents high alpha magnitude. The basic bar
feedback is shown in Figure |nbsp|
:num:`fig-early-prototype-feedback-box`. Inspired by the Smartphone Brain
Scanner alpha feedback training app (Section |nbsp|
:ref:`ch-background-smartphone-brain-scanner-2`) - which included another
feedback in which performance history was visible - we implemented a version of
each interface showing recent performance history of a sliding time frame of 30
seconds.

In the case of the box feedback, history was visible in the frame color - see
Figure |nbsp| :num:`fig-early-prototype-feedback-box-w-history`. In the case of
the bar, we implemented performance history in the form of a horizontal line
showing performance history of a 30 seconds sliding time frame. Additionally, we
visualized performance history of the entire training session in the form of
background color changes - see Figure |nbsp|
:num:`fig-early-prototype-feedback-bar-w-history`. From our initial experience
with the feedback bar, we thought the rather violent movements from low to high
due to the intrinsic variance in alpha magnitude might introduce EOG
noise. Therefor we made another variation of the bar interface in which the bar
only grows. High alpha magnitudes makes it grow fast while low alpha magnitudes
slows the growing down or stops it completely (Figure |nbsp|
:num:`fig-early-prototype-feedback-bar-growing`).

In sum, the prototype featured: (*i*) alpha feedback training through 5
different feedback views; (*ii*) individual alpha peak detection; (*iii*) alpha
feedback training based on flexible alpha band definition; and (*ii-ii*) a view
showing performance history in a plot (Figure |nbsp|
:num:`fig-early-prototype-screen-history`).

Using the app relied on the following sequence of actions:

1. The user should turn on and mount the MindWave BCI and launch the Android
   application prototype.

2. The user should calibrate according to the individual alpha peak which is
   done by pushing the "Calibrate" button. The alpha peak frequency is used to
   delimit the alpha band for which to give feedback on.

3. The user should record a baseline while under influence of random feedback
   which is done by pushing the "Baseline" button. The baseline is used in
   mapping the current alpha level to a feedback state. Furthermore, the
   baseline recordings are used to track alpha activity gains over time, the
   *training effect* of using AlphaTrainer.

4. The app is now ready for training which is started by pushing the "Feedback"
   button.


The prototype app uses standard Android UI components (see Figure |nbsp|
:num:`fig-early-prototype-app-screen-start`) and the interaction form is manual
as it is clear from the training procedure listed above. In designing and
building the prototype we thought in terms of *availability* regarding app
functionality and the information dimensions present in the feedbacks (for
example feedbacks showing current alpha state + performance history).


.. Note: we have to be pragmatic here with the figure texts they have to be short
.. to remain of one page which is important for the overview.

.. subfigstart::

.. _fig-early-prototype-app-screen-start:

.. figure:: fig/early-prototype-app-screen-start.png
    :alt: Start screen 
    :width: 80%
    :align: center
    
    Early prototype app screen start.

.. _fig-early-prototype-screen-calibrate:

.. figure:: fig/early-prototype-screen-calibrate.png
    :alt: Calibration screen
    :width: 80%
    :align: center
    
    Calibration screen.

.. _fig-early-prototype-feedback-box:

.. figure:: fig/early-prototype-feedback-box.png
    :alt: Feedback box 
    :width: 80%
    :align: center
    
    Feedback box.

.. _fig-early-prototype-feedback-box-w-history:

.. figure:: fig/early-prototype-feedback-box-w-history.png
    :alt: Feedback box with history 
    :width: 80%
    :align: center
    
    Feedback box with history. Green is current feedback and border is history.

.. _fig-early-prototype-feedback-bar:

.. figure:: fig/early-prototype-feedback-bar.png
    :alt: Feedback bar
    :width: 80%
    :align: center
    
    Feedback bar goes up and down based on alpha level.


.. _fig-early-prototype-feedback-bar-w-history:

.. figure:: fig/early-prototype-feedback-bar-w-history.png
    :alt: Feedback bar with history
    :width: 80%
    :align: center
    
    Feedback bar with history.

.. _fig-early-prototype-feedback-bar-growing:

.. figure:: fig/early-prototype-feedback-bar-growing.png
    :alt: Feedback bar growing
    :width: 80%
    :align: center
    
    Feedback bar growing gradually based on the summed alpha.

.. _fig-early-prototype-screen-history:

.. figure:: fig/early-prototype-screen-history.png
    :alt: History screen
    :width: 80%
    :align: center
    
    History screen: Baselines (black dots) and feedbacks (red dots).

.. subfigend::
    :width: 0.30
    :alt: Screen shoots from early Android prototype
    :label: fig-early-prototype
    
    Screenshots from the early prototype Android application using default Android UI components and manual interaction.


We tested the prototype informally on ourselves, fellow students, friends and a
domain expert within BCI and HCI. From our testing three notions became clear.

First, we had to revisit our manual interaction and focus on *accessibility*
regarding app functionality. It is not enough that the individual alpha peak can
be determined, baseline can be recorded, etc. when relying on the user to
calibrate (twice a day) and record baseline (once a day) - the user should not
even have to know about these concepts. We shifted our focus from *availability*
to *accessibility* in delegating the responsibility of taking appropriate
actions to the app by means of a proactive interaction described below in the
design of AlphaTrainer (Section |nbsp| :ref:`ch-design-alphatrainer`).

Second, we gained several important insights about the 5
feedbacks. Interestingly, the bar height was perceived inversely proportional to
how it was designed. By design, a high bar represents high alpha from an alpha
performance metaphor "more alpha is good". However, some subjects experienced
the interface expressing state of mind from a "low mind activity is good" where
the obvious goal state of the feedback would be a low bar. We adopted the latter
metaphor when designing a new set of feedbacks for the next generation of
interfaces. However, the bar was generally experienced to be unpleasant for
other reasons - namely due to its radical shifts - why we excluded it from this
point. During the testing of the prototype, the idea of supporting other
modalities than sight was generated. This expanded the design space of the
feedbacks and led to the development of audio and tactile feedbacks. We ended
out with a set of 5 feedbacks: 2 visual (1 with history), 2 auditive (1 with
history) and 1 tactile. They are described below in the design of AlphaTrainer
(Section |nbsp| :ref:`ch-design-alphatrainer`).

Third, we learned that the immediate impression of the app through the UI design
was an important part of the general experience of using the app. When
non-developers tried the prototype, they responded negatively to the standard
Android layout (see Figure |nbsp| :num:`fig-early-prototype-app-screen-start`)
which looks a lot more rough than they are used to from other apps.  We noted
that the general user is not able to abstract away from the graphical
layout. Since we wanted to deploy the app for real world usage, we wanted to
remove this obstacle of users distancing from the app due to its
layout. Assisted by a digital designer, we updated the graphical design.  The
result can be seen below in the final design of AlphaTrainer (Figure |nbsp|
:num:`fig-final-prototype-app-flow`).

Finally the last iteration of our prototype consisted of a test and analysis by
an interaction design expert and a pilot evaluation performed by our
selves. This had a set of concrete outcomes:

- The app should yield training performance immediately after a training has
  been performed.
- When headset connection fails, try to reconnect and/or show the user as
  precise as possibly where the problem is.
- History of training performance should be kept in the simple app design with a *high
  ink-to-information ratio* |nbsp| :cite:p:`tufte_envisioning_1990`.

This ends our chronological journey through the design process. We now move
on to describe the AlphaTrainer system in its current state
- the version used in the user evaluation (Chapter |nbsp| :ref:`ch-evaluation`).


.. _ch-design-alphatrainer:

AlphaTrainer
============

.. AlphaTrainer (current result / state) 

.. a. tool 
.. b. 3 modalities / 5 feedbacks 
.. c. history

.. Explanation of the final AlphaTrainer design.

.. Robust and easy to use

.. App is a tool for serious trainers - not a mindfulness lotus flower
.. app.
.. - Greek alpha logo which is probably known by its user + pharmacy-like
..   toned down digital design
.. - performance in numbers/graphs, not making a meditation flower grow


This chapter concludes with a description of the resulting AlphaTrainer
prototype design. When the app is launched, the user is met by the home screen
(Figure |nbsp| :num:`fig-final-prototype-app-flow-app-screen-start`). The home
screen contains a logo and the 3 buttons: "Training", "History" and
"Settings". The logo is the Greek letter alpha, which we imagine the user of
AlphaTrainer (our personas) might recognize. The colors form a toned down blue
palette and in conjunction with the logo we aim at conveying that AlphaTrainer
is a serious tool.


.. Note: we have to be pragmatic here with the figure texts they have to be short
.. to remain of one page which is important for the overview.

.. subfigstart::

.. _fig-final-prototype-app-flow-app-screen-start:

.. figure:: fig/final-prototype-start.png
    :alt: Start screen 
    :width: 80%
    :align: center
    
    Start screen.


.. _fig-final-prototype-app-flow-calibrate-step-1:

.. figure:: fig/final-prototype-calibrate-step-1.png
    :alt: Calibrate step 1
    :width: 80%
    :align: center
    
    Calibrate step 1.


.. _fig-final-prototype-app-flow-calibrate-step-2:

.. figure:: fig/final-prototype-calibrate-step-2.png
    :alt: Calibrate step 2
    :width: 80%
    :align: center
    
    Calibrate step 2.


.. _fig-final-prototype-app-flow-calibrate-no-connect:

.. figure:: fig/final-prototype-calibrate-no-connect.png
    :alt: Not connected
    :width: 80%
    :align: center
    
    Not connected (headset).


.. _fig-final-prototype-app-flow-no-headset-found:

.. figure:: fig/final-prototype-no-headset-found.png
    :alt: No headset found
    :width: 80%
    :align: center
    
    No headset found.


.. _fig-final-prototype-app-flow-prototype-reference:

.. figure:: fig/final-prototype-reference.png
    :alt: Start reference recording
    :width: 80%
    :align: center
    
    Start ref. recording.


.. _fig-final-prototype-app-flow-training-start:

.. figure:: fig/final-prototype-training-start.png
    :alt: Training feedback instructions
    :width: 80%
    :align: center
    
    Training feedback instructions.


.. _fig-final-prototype-app-flow-training-completed:

.. figure:: fig/final-prototype-training-completed.png
    :alt: Training completed
    :width: 80%
    :align: center
    
    Training completed.


.. _fig-final-prototype-app-flow-training-history:

.. figure:: fig/final-prototype-history-overview.png
    :alt: Training history
    :width: 80%
    :align: center
    
    Training history (per day, week and month). Plots the last 10 feedback
    recordings and the last 5 reference recordings.


.. subfigend::
    :width: 0.30
    :alt: Screen shoots from the app flow of the final AlphaTrainer Android prototype
    :label: fig-final-prototype-app-flow
    
    Screen shoots from the app flow of the final AlphaTrainer Android 
    prototype.


When the user clicks "Training", the app takes on a proactive interaction. It
decides whether it needs to calibrate or to record a baseline before training
can be performed. The appropriate action is decided from these rules: (*i*) if
calibration has not been performed within 8 hours, calibrate now; (*ii*) if a
baseline has not been recorded today, record one now; finally (*iii*) if the first two
criteria are met, the user is set to perform alpha feedback training.  The
headset connection status is shown in top of the screen both as a number (0 -
100%) and by a color varying between red (0%) over yellow (between 0% and 100%)
to green (100%) (Figure |nbsp|
:num:`fig-final-prototype-app-flow-calibrate-step-1`). While connection is not
yet established, the button for starting the appropriate action is grayed
out. Should connection to the headset fail, the app will try its best to tell
the user what the problem is - for example in case the headset is turned off
(Figure |nbsp| :num:`fig-final-prototype-app-flow-calibrate-no-connect`). The
app continuously tries to establish connection while being inside the "Training"
area.

When ready to perform alpha feedback training, the app looks up which feedback
has been selected in the settings. The trainees objective is presented,
e.g. "Relax and turn the box green" in case of the box changing colors feedback
mentioned earlier. We ended up with 5 different feedbacks:

1. Box changing colors. This feedback contains no performance history (Figure
   |nbsp| :num:`fig-final-prototype-feedback-1-box-colors`).

2. Circles that move according to alpha level from the logic that high alpha
   amplitude (quiet state of mind) makes circle movement less. The circles are
   affected by gravity which conveys the recent performance history - when alpha
   level increases, it takes some time for the circles through the gravity to
   reach a state in which they are still (Figure |nbsp|
   :num:`fig-final-prototype-feedback-2-circles`).

3. Vibration feedback in which high alpha amplitude makes the phone vibrate
   less. This feedback contains no performance history (Figure |nbsp|
   :num:`fig-final-prototype-feedback-3-4-5`).

4. Tone generator in which the pitch of the tone represents the current alpha
   level from the logic that high alpha amplitude (quiet state of mind) lowers
   the pitch. This feedback contains no performance history (Figure |nbsp|
   :num:`fig-final-prototype-feedback-3-4-5`).

5. Bell sounds appearing in which the number of bells represent the alpha level
   from the logic that high alpha amplitude (quiet state of mind) makes a quiet
   sound scape by having fewer bell sounds appear. When alpha level increase, it
   takes some time for the bell sounds to disappear. Thereby the duration of the
   bell sounds convey performance history (Figure |nbsp|
   :num:`fig-final-prototype-feedback-3-4-5`).


.. subfigstart::

.. _fig-final-prototype-feedback-1-box-colors:

.. figure:: fig/final-prototype-feedback-1-box-colors.png
    :alt: Feedback 1 with changing colors.
    :width: 80%
    :align: center
    
    Feedback 1 with changing colors objective is to turn the color 
    green (from red).


.. _fig-final-prototype-feedback-2-circles:

.. figure:: fig/final-prototype-feedback-2-circles.png
    :alt: Moving circles.
    :width: 80%
    :align: center
    
    Feedback 2 with moving circles - objective less movements.


.. _fig-final-prototype-feedback-3-4-5:

.. figure:: fig/final-prototype-feedback-3-4-5.png
    :alt: Vibration, tone generator and bell sounds.
    :width: 80%
    :align: center
    
    Vibration, tone generator and bell sounds - they all share the 
    same screen instruction. Objectives make less vibration, lower 
    pitch of tone and less bells.

.. subfigend::
    :width: 0.30
    :alt: Screen shoots from the 5 feedbacks of the final Android prototype.
    :label: fig-final-prototype-app-feedbacks
    
    Screen shoots from the 5 feedbacks of the final AlphaTrainer Android prototype.


After a training has been performed, the user is immediately presented with a
number representing performance in percent. This number is calculated by comparing the
currently ended training session to the most recent training before that (Figure
|nbsp| :num:`fig-final-prototype-app-flow-training-completed`). The user can
then choose to train again by pushing the "Try again" button. This concludes the
"Training" area of the app.

When the user selects "History" from the home screen, she is presented with a
simple history dashboard (Figure |nbsp|
:num:`fig-final-prototype-app-flow-training-history`). The training performance
of current day, current week and current month is presented in the top and
conveys the set of trainings compared to all training sessions performed. The
dashboard also has two simple graphs showing the recent training sessions and
the recent baseline recordings.

When the user selects "Settings" from the home screen, she is presented with a
conventional Android settings screen which enables her to choose among the 5
feedbacks described above.


We have now presented the AlphaTrainer and are now ready to cover the actual
implementations in detail in Chapter |nbsp| :ref:`ch-implementation`.


.. rubric:: Footnotes

.. [#foot-background-hjernetraening] `<http://www.hjernetraening.dk>`_

