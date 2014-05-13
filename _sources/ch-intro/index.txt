.. _ch-intro:

==============
 Introduction
==============


.. _ch-intro-neurofeedback-stress-and-bci:

Neurofeedback, stress and brain-computer interfaces
===================================================

Neurofeedback training (or neurofeedback therapy) is based on giving real time
feedback on brain activity. This feedback enables the brain to navigate towards
some desired brain state. Certain brain states have been shown to be
positively correlated with cognitive performance, de-stressing etc. Such brain
states form the goal for the neurofeedback.

Stress - a big and growing problem to both society and individuals -
is one of the conditions neurofeedback therapy is targeting within a
clinical context. For example, it is used within the US army as treatment
for veteran soldiers suffering from post-traumatic stress disorder
(PTSD) |nbsp| :cite:p:`white_alphatheta_2009`. However,
neurofeedback systems targeting consumers remain rare and expensive
due to the required specialized hardware - in order to sense brain
states, a neurofeedback system includes a Brain-Computer Interface
(BCI). Though most BCIs are expensive and aimed at professionals,
within recent years a number of BCIs targeting consumers with prices
starting from $ 50,- have emerged. Interaxon's *Muse* |nbsp|
[#foot-intro-interaxon]_ BCI exemplifies the new generation of
discrete consumer BCIs (Figure |nbsp| :num:`fig-muse-headband`).

.. _fig-muse-headband:

.. figure:: fig/muse-headband-collage.png
    :alt: Muse consumer BCI
    :width: 80%
    :align: center
    
    Muse consumer BCI (Image courtesy of Interaxon).


The combination of the emerging consumer interfaces and the prospects of
neurofeedback motivates our hypothesis.


.. _ch-intro-hypothesis-goals:

Hypothesis
==========

We hypothesize that it is feasible to build a neurofeedback system comprising of
a consumer BCI and a mobile device which will enable neurofeedback training in
an everyday setting.

To test our hypothesis, we have set the following goals:

G1

    Evaluate relevant consumer BCI's feasibility for neurofeedback training.

G2

    Design, implement and evaluate AlphaTrainer - a system enabling
    neurofeedback training in an everyday setting.

If such a system shows feasible, it would enable wide adoption of
neurofeedback training in eliminating the obstacle of expensive hardware. This
could move the neurofeedback practice out of a clinical setting and into the
homes and workplaces of people motivated to reduce their stress.

.. We speculate that such a system could be adopted by a group of
.. busy

.. We imagine that such a system would be valuable for a large group of
.. busy people motivated to reduce their stress.



.. _ch-intro-method:

Method
======

The vision and goal of AlphaTrainer - to enable neurofeedback training in an everyday
context - is rooted in the ideas of the early pioneers of ubiquitous computing
(ubicomp) who envisioned invisible computing, prototypes and the move away
from desktop computers into devices that "*weave themselves into the fabric of
everyday life*" |nbsp| :cite:p:`weiser_computer_1991` |nbsp|
:cite:p:`weiser_world_1994` |nbsp| :cite:p:`weiser_computer_1999`.

In short, our method is to design, implement, deploy and evaluate
AlphaTrainer. This approach is inspired by later adapters of ubicomp stressing
the importance of deploying working systems for real usage. For example, Bardram
and Friday argue that "*...  the most valuable lessons to take from looking at
successful ubicomp systems is the need to mature the system through actual use*"
|nbsp| :cite:p:`bardram_ubiquitous_2010`. By deploying AlphaTrainer for actual
use in an everyday context, we are able to learn about the system and
the usage "*in situ*" which can not be investigated in a lab or by means of
lo-fi prototypes.
 
The process of building AlphaTrainer involves several activities. Which can be
mapped and understood through a framework proposed by Mackay and Fayard |nbsp|
:cite:p:`mackay_hci_1997`. The framework explains how HCI research can benefit
from triangulating across science and design disciplines while continuously
producing artifacts. Figure |nbsp| :num:`fig-triangulation` outlines the major
activities of this thesis. The arrows between activities show when output of
one activity has been fed into another thus mapping how activities have
benefited from each other across disciplines.


.. _fig-triangulation:

.. figure:: fig/triangulation.png
    :alt: Mapping of activities in the thesis activities and process
    :width: 100%
    :align: center
    
    Mapping of the thesis activities and process - applying the triangulation 
    framework proposed by Mackay and Fayard |nbsp| :cite:p:`mackay_hci_1997`.


.. _ch-intro-thesis-overview:

Thesis overview
===============

We outline the structure of this thesis below based on the thesis activities
mapped in Figure |nbsp| :num:`fig-triangulation`.

In Chapter |nbsp| :ref:`ch-background` we establish a broad overview of
BCIs and neurofeedback training. The chapter describes related consumer
products and related works within the area of consumer BCIs and
neurofeedback. This is the foundation of our hypothesis and it frames
*Neurofeedback theory* and *Investigate current neurofeedback systems*.

Chapter |nbsp| :ref:`ch-experiment` describes the design of the *Experimental
prototype* and the *Evaluation of consumer BCIs* within the designed
experiment. This evaluation addresses our first goal - **G1** (Section
|nbsp| :ref:`ch-intro-hypothesis-goals`). The gained knowledge of the BCIs
capabilities leads us to a *Revised Hypothesis*
which enables us to develop the system design in the next chapter.

The *Design and implementation of AlphaTrainer* is split in two chapters.
Chapter |nbsp| :ref:`ch-design` outlines the design activities, decisions and
process that lead us to our final design, while Chapter |nbsp|
:ref:`ch-implementation` covers the implementation of the AlphaTrainer system.

In Chapter |nbsp| :ref:`ch-evaluation` we evaluate the system through a
*User Evaluation of AlphaTrainer*. The chapter addresses directly our
second goal - **G2** (Section |nbsp| :ref:`ch-intro-hypothesis-goals`) and leads
us to a *Verified Hypothesis* and a *Revised AlphaTrainer design*.

Finally we make out the conclusion and outline future works - Chapter |nbsp|
:ref:`ch-conclusion`.


.. _ch-intro-limitations:

Limitations
===========

This thesis does not attempt to make any clinical claims about AlphaTrainer's
efficacy regarding stress treatment. Nor does it address the security aspects
of data management which would be required for a system for clinical use.

Rather, it explores whether a neurofeedback system can actually be build
using a mobile device and a low-cost consumer BCI. Furthermore, it explores
through real world deployment of a prototype whether it makes sense for users
to perform neurofeedback training in an everyday context.


.. rubric:: Footnotes

.. [#foot-intro-interaxon] `<http://www.interaxon.ca>`_
