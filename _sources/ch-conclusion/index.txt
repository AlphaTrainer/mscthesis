.. _ch-conclusion:

============
 Conclusion
============

This thesis has examined the feasibility of building a system comprising of a low cost consumer BCI and a mobile device which enables alpha feedback training embedded in everyday life. We started our investigations by evaluating three consumer BCIs of interest - especially regarding their ability to measure alpha waves. Based on the results, we chose to use the MindWave Mobile BCI since it is able to measure alpha and is the best exponent for the next generation of consumer BCIs.

We continued our investigation by designing, implementing and evaluating AlphaTrainer, an Android based alpha feedback training system. The AlphaTrainer app features:

- Neurofeedback with multiple modalities (vision, audio and tactile).
- Analysis of raw EEG data which enables feedback on individually determined frequency bands.
- Performance history tracking.
- Proactive interaction which keeps track of when to calibrate and record baseline.
- A modular architecture which enables addition of headsets, data processing modules and feedbacks.

We performed a real world evaluation in which 4 evaluation participants used AlphaTrainer for a week at home, at work and while traveling. We learned that:

- The participants experienced using AlphaTrainer to be immediately rewarding and perceived the training practice as a de-stressing exercise.
- Participants were generally positive about using AlphaTrainer and could see themselves use it and even buy a BCI in order to perform alpha training.
- The data collected during the evaluation indicates that AlphaTrainer deployed in a real world scenario is able to measure alpha and that the feedback mechanism increases alpha.
- The AlphaTrainer system performed as expected during the evaluation without noticeable technical problems.

From the evaluation results we are able to verify our hypothesis and conclude that *it is possible to build a neurofeedback system comprising of a consumer BCI and a mobile device*.

An interesting next step would be to investigate the training effect of using AlphaTrainer over a longer period of time. Though this is deemed out of scope in this thesis, we have initiated the first steps to make such an investigation. We have done so by planning a release of AlphaTrainer during December 2013 to the *Google Play Store* [#foot-conclusion-play-store]_.

.. While AlphaTrainer can be downloaded and used for free, the user pays by letting us collect anonymous training data from the usage to a scalable cloud service.


.. _sec-future-work:

Future work
===========

In the short term, we will finish an iteration of the AlphaTrainer design taking the concrete outcomes of the user evaluation as input.


In the long term, it would be interesting to investigate the efficacy of AlphaTrainer. As mentioned above, the AlphaTrainer app support data collection which enables anonymous tracking of individual development in alpha levels over time. Still, this method would not conclusively answer whether any observed increase in alpha was caused by the feedback mechanism - for example, an increase in alpha could be caused by just taking the time to relax, by a method (such as meditation) performed while using AlphaTrainer or some unrelated change in the subjects situation. The neurofeedback component of AlphaTrainer could be isolate and investigated in a controlled longitudinal study including three groups: (*i*) one group would perform alpha feedback training; (*ii*) a "placebo" group would think they performed alpha feedback training but without actually controlling the feedback (which could for example be pre-programmed); finally (*iii*) a third group would perform a control activity i.e. performing a de-stressing breathing exercise or just lying comfortably on the floor while getting their EEG activity measured. These three groups would perform an equal amount of their activities respectively over a substantial period of time. Comparing the development in baseline alpha levels between the groups would inform about the efficacy of the neurofeedback component of AlphaTrainer.


If AlphaTrainer in conjunction with the MindWave BCI - the configuration investigated in this thesis - turns out not to be effective, it would be interesting to see how it performs with future headsets. Same thing goes for new feedbacks and processing modules which are replaceable due to the modular architecture of AlphaTrainer. We speculate that a consumer BCI headset, at some point at least, will meet the requirements for neurofeedback training. This point illustrates that this thesis' contribution of designing, implementing and evaluating AlphaTrainer still has value should the case be that the current MindWave configuration of AlphaTrainer turn out not to be efficacious.


If (or when) AlphaTrainer on the other hand turns out to be effective, it opens up to a lot of exciting future research. It would be extremely interesting to investigate how AlphaTrainer or the neurofeedback principles of the AlphaTrainer app might fit in a clinical context. For example, patients could be ordered neurofeedback training on their phone as part of their treatment. This would give the patients the convenience of performing neurofeedback training where and when it fits them best. Clinical professionals would be able to monitor the training progress. The system could include an event model in which a clinical professional would be notified if a certain patterns in the training data occurred. The frequency band on which the feedback is given (the alpha band in case of AlphaTrainer) could be changed in order to widen the neurofeedback application areas to for example ADHD in which case beta and theta frequency bands are often the basis for neurofeedback training.


.. In a telemedicin Port it to iOS (Windows Phone ?) in order to broaden potential users - Monarch ref saying people need to be able to use the phone they are used to. This should be easy due to modularity e.g. native signal processing lib, feedbacks using web technologies etc.

.. In a consumer context, neurofeedback training as expressed in AlphaTrainer could benefit from different trends. As it became apparent during the evaluation, AlphaTrainer is experienced as being among a trend of de-stressing tools and methods for which Mindfulness is an exponent. Furthermore, AlphaTrainer fits very well among the goals within the quantified self movement. We expect that AlphaTrainer could potentially have a wide adoption potential which is supported by our evaluation.


In a consumer context, it is an open and exiting question whether there is a base for adopting neurofeedback training as it is expressed in AlphaTrainer and how this potential consumer base develop over time when new generations of consumer BCIs appear. The evaluation hints that there could be a potential for AlphaTrainer adaptation - at least our 4 test participants found value in using AlphaTrainer. To further investigate this potential, our plan is to collect as much data as possible when releasing AlphaTrainer for free (or rather letting users pay with anonymous data) to the Google Play Store. This data, usage patterns and user feedback is valuable and could lead to the development of the next generation of AlphaTrainer, which might realize some commercial potential.

.. From the collected usage patterns and feedback it would be decided which business model would best fit such a 

The vision for AlphaTrainer's future is to put the prospects of neurofeedback into the hands of everyone with a smart phone and a low-cost consumer BCI.


.. rubric:: Footnotes

.. [#foot-conclusion-play-store] `<https://play.google.com>`_
