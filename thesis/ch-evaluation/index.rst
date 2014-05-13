.. _ch-evaluation:

==================
 User evaluation
==================

.. Objective
.. =========

The evaluating of AlphaTrainer seeks to validate its design and investigate whether AlphaTrainer actually enables alpha feedback training in an everyday context. We derived a set of research questions targeting *A* the AlphaTrainer design and *B* its use in context:

*A*: How is training perceived and affected by specific feedbacks?

- are specific feedbacks perceived to be more pleasant/precise/etc than others?
- does specific feedbacks enable/disable training in certain situations?

*B*: How does alpha feedback training on a mobile device fit into an everyday context?

- is it hard to make time/room for training?
- are there (practical) obstacles for alpha feedback training in an everyday context?
- is alpha feedback training perceived to be rewarding or hard work?




**Limitations and scope**

The biggest limitation of this evaluation lies in the number of evaluation participants. Due to the hardware dependency on a BCI, we can only involve a limited number of participants. We have 2 such interfaces at our disposal which means we can run our study with 2 participants at a time. We have chosen a duration of 1 work week per participant and we will run the evaluation for 2 weeks which gives us a total of 4 participants only.

In regard to initially verifying the *design* of AlphaTrainer, we can gain useful data from even a few number of participants. For example, it is argued by Virzi that 4 participants is enough to uncover 80% of a systems usability problems |nbsp| :cite:p:`virzi_refining_1992`. We compensate for the low number of participants by collecting both quantitative, qualitative and logged data.

Regarding the 
*usage in context*, 4 participants are too few to represent a target group. Accordingly, we will treat the evaluation findings only as an initial hint as to whether it makes sense for people to perform alpha training in an everyday setting on a mobile device.

We will not try to make any statistical arguments based on data collected from our 4 evaluation participants. However, we still collect and discuss numerical data but only to look for hints and suggestions.


The evaluation participants are acquaintances of us which carries the possibility that they are biased and want to "perform good". We will convey to our best ability that anything negative they might experience is valuable information to us. Furthermore, we will keep this potential bias in mind while observing and interviewing them.


Since we want to learn about the effects of different feedbacks, we choose a factorial experiment |nbsp| :cite:p:`mackenzie_human-computer_2013` in which the different *feedbacks* are independent variables (i.e. factors). This is somehow a trade-off since a longitudinal study |nbsp| :cite:p:`mackenzie_human-computer_2013` in which the *amount of practice* is the independent variable would have been exiting as well. We choose the former since a week is a very short period anyway for a longitudinal study trying to establish a training effect. As mentioned in the Background Chapter |nbsp| :ref:`ch-background`, neurofeedback training typically involves 40-80 sessions of 45-60 minutes duration. Thus, the investigation of training effect is deemed out of scope in this evaluation. We will pick up the challenge of setting up an experiment to document the training effect of AlphaTrainer in the Future Works Section |nbsp| :ref:`sec-future-work`.


Method
======

Before the experiment start, we met with each test subject to install AlphaTrainer on his phone (participant 3 + 4) or hand out a phone with AlphaTrainer installed (participant 1 + 2). The test subject is also handed out a MindWave BCI and instructed how to use the system, connect to the headset etc. in order to abstract away any learning curve of the system.

In order to learn about the different feedback types and modalities, the participants are instructed to change feedback every day according to a schema which is also handed out before experiment start (Appendix |nbsp| :ref:`appendix-final-evaluation`). To avoid order effects, the distribution of feedbacks across the participants is balanced as shown in Table |nbsp| :num:`table-latin-square-feedbacks`.

.. figtable::
    :label: table-latin-square-feedbacks
    :alt: The distribution of feedbacks across participants during their 5 days of training
    :caption: The distribution of feedbacks across participants during their 5 days of training.
    :spec: r l l l l l
    :nofig:

    +-------------+-----------+-----------+-----------+---------+-----------+
    | Participant | Day 1     | Day 2     | Day 3     | Day 4   | Day 5     |
    +=============+===========+===========+===========+=========+===========+
    | 1           | Box       | Vibration | Bells     | Circles | Tone      |
    +-------------+-----------+-----------+-----------+---------+-----------+
    | 2           | Vibration | Circles   | Box       | Tone    | Bells     |
    +-------------+-----------+-----------+-----------+---------+-----------+
    | 3           | Circles   | Tone      | Vibration | Bells   | Box       |
    +-------------+-----------+-----------+-----------+---------+-----------+
    | 4           | Tone      | Bells     | Circles   | Box     | Vibration |
    +-------------+-----------+-----------+-----------+---------+-----------+


The experiment lasts for 5 working days in which the subjects are committed to perform at least two training sessions per day - preferably one training within a working context and one in a home context. Before initiating the evaluation, we ran a pilot for a week on ourselves in order to catch any experiment flaws and to validate the Android application robustness.

During the 5 days of the experiment, we collect data in the following ways: (*i*) survey;
(*ii*) participant observation and a semi-structured interview; and (*iii*) data logging.


Survey
------

The participants are asked to answer a small questionnaire after each AlphaTrainer usage (Appendix |nbsp| :ref:`appendix-final-evaluation`). A 5-point Likert scale is used, in which participants mark their agreement with the statements below from 1 (strongly agree) to 5 (strongly disagree) :cite:p:`lazar_research_2010`. 

The first statement target the perceived relaxation benefit feedback type/modality:

1. I feel more relaxed after training than before

The next statements target the specific feedback type/modality:

2. The feedback was pleasant
3. The feedback was precise

The next 3 statements target the training in context:

4. I was disturbed by my surroundings
5. My surroundings were disturbed by me
6. It was easy to find time for training

The final statement targets the comfort of the MindWave headset:

7. It was comfortable to wear the headset


Participant observation and a semi-structured interview
-------------------------------------------------------

Since alpha training in an everyday setting is not a well understood activity, we can not be sure which interesting issues could arise let alone capture them through a survey. Therefor we observe the participants while they perform their training which enables us openly to address the issues that might arise. Observing is done via *Skype* which is both more flexible (we can sit "stand by" until the participant is ready to train) and less intrusive for the training practice than if we were sitting next to the participant in their home or at their work.

While observing the training, we pay attention to: (*i*) interaction with app/headset, how is it used?; (*ii*) interaction with surroundings, does something enable/disable training?; and (*iii*) anything that has influence on the training.

We write notes while observing and anything interesting can be followed up in a short semi-structured post training interview structured by this brief interview guide: (*i*) follow up on observations; (*ii*) how was the training experience?; (*iii*) did the setting make a difference?; (*ii-ii*) did the feedback make a difference?; and (*v*) when and how have you been training since last time?


Data logging
------------

While performing alpha feedback training, the processed training data and meta data (e.g. alpha levels, feedback type, etc.) is: (*i*) posted to a web service (Section |nbsp| :ref:`ch-implementation-alphatrainer-cloud-based-storage`); and (*ii*) stored locally on the phone as processed alpha levels along with the raw EEG data (Section |nbsp| :ref:`ch-implementation-models-persistent-storage`). The collection of this data enables us to look for hints as to whether the system works as expected. E.g. it is expected that: (*i*) baseline alpha levels are generally higher when participants have closed eyes; and (*ii*) alpha levels are higher when the user actually controls the feedback compared to the baseline recording of the same feedback (feedback effect).

Furthermore, the raw EEG enables us to follow up on unexpected results in pursuit of what might be the cause (e.g. noise).


Participants
============

The participants are chosen among our acquaintances matching our target group - manifested in our personas - as much as possible (Section |nbsp| :ref:`ch-design-model-and-method`). They have been guaranteed anonymity in this thesis and have verbally agreed that we can use the data collected during the evaluation and show their photo. They count 3 males and 1 female with an average age of 33 years.


Result
======

After two weeks of evaluation we got 4 sets of data each including observation notes, semi-structured interview notes, questionnaires and the logged training data. The survey results are first presented and discussed. Then we move on to present the most important notions from the observations and interviews after which we present some insights from the logged data.

In total, 63 training sessions and 19 baselines were performed and 39 questionnaires were answered.


Survey results
--------------

To get an overview of the results, we have calculated mean and standard deviation of the questionnaire answers. One participant missed a training during the evaluation so the results are based on 39 filled out questionnaires. The results are shown in Table |nbsp| :num:`table-micro-questionary-result`


The first statement **I feel more relaxed after training than before** relates to the immediately experienced effect of performing alpha training. It shows us that the participants were generally feeling slightly more relaxed after training. This does not vary significantly over the different feedbacks which could suggest that the main source of the increased relaxation is to be found in something general for the alpha training practice. That alpha training is perceived to be immediately rewarding is backed up by several observations during the evaluation period. For example, participant 1 stated that she experienced to become very relaxed using AlphaTrainer when training at work (she is a teacher and trained in her classroom). She also used it as a way to stress down when she got home after work.


The next 2 statements **The feedback was pleasant** and **The feedback was precise** relates to how the specific feedbacks were experienced. The Box and the Bells feedbacks are generally perceived to be a little less pleasant then the others. Looking at the std.dev. these two feedbacks are also the ones causing greatest division between the participants. Again, this is backed up during observations where participant 3 describes the Bells feedback as the best metaphor for training relaxation while participant 4 states that he got a shock whenever a bell sound was triggered. Regarding precision, the results are quite similar - the Box and the Bells feedbacks are perceived slightly less precise. Overall, the two questions do not reveal big differences between the feedbacks, rather that the participants had different feedback preferences.


The next 3 statements - **I was disturbed by my surroundings.**, **My surroundings were disturbed by me** and **It was easy to find time for training** - relates to the usage of AlphaTrainer in context. It appears that the participants were at times slightly disturbed by their surroundings and that the degree varies between trainings and participants. It also appears that the participants were hardly disturbing their surroundings. In general across all training sessions the participants found it quite easy to find time for training though this also varied some between the trainings. This means that if they only had to train once a day - which a participant mentioned during observations would be more natural than 2 times a day - it would become easy to find the time.


The answers to the final statement **It was comfortable to wear the headset** informs us that the participants were generally perceiving the MindWave as neutrally comfortable (which matches the findings in the BCI Evaluation Chapter :ref:`ch-experiment`) and thereby not a significant obstacle for the participants' usage of AlphaTrainer.


.. figtable::
    :label: table-micro-questionary-result
    :caption: Post training survey results showing the degree to which participants agree with the statements from 1 (strongly agrees) to 5 (strongly disagree). Results are based on 4 participants answering a total of 39 questionnaires.
    :alt: Result of survey
    :spec: >{\raggedright\arraybackslash}p{0.30\linewidth} p{0.10\linewidth}  p{0.10\linewidth}  p{0.10\linewidth}  p{0.10\linewidth}  p{0.10\linewidth} 
    :nofig:

    +----------------------------+----------+----------+----------+----------+----------+
    |Statement                   |Box       |Vibration |Circles   |Tone      |Bells     |
    +============================+==========+==========+==========+==========+==========+
    |**I feel more relaxed after |2.1 ±0.4  |2.1 ±0.4  |2.5 ±0.5  |2.0 ±0.8  |1.8 ±0.4  |
    |training than before.**     |          |          |          |          |          |
    |                            |          |          |          |          |          |
    +----------------------------+----------+----------+----------+----------+----------+
    |**The feedback was          |2.6 ±1.0  |2.1 ±0.6  |2.0 ±0.9  |1.9 ±0.7  |2.7 ±1.4  |
    |pleasant.**                 |          |          |          |          |          |
    |                            |          |          |          |          |          |
    |                            |          |          |          |          |          |
    +----------------------------+----------+----------+----------+----------+----------+
    |**The feedback was          |2.7 ±0.8  |2.2 ±0.7  |2.1 ±0.6  |2.1 ±0.9  |2.5 ±1.0  |
    |precise.**                  |          |          |          |          |          |
    |                            |          |          |          |          |          |
    +----------------------------+----------+----------+----------+----------+----------+
    |**I was disturbed by my     |3.7 ±1.0  |2.6 ±1.2  |2.4 ±1.4  |2.4 ±1.0  |3.5 ±1.2  |
    |surroundings.**             |          |          |          |          |          |
    |                            |          |          |          |          |          |
    +----------------------------+----------+----------+----------+----------+----------+
    |**My surroundings were      |4.4 ±0.5  |4.2 ±1.0  |3.9 ±1.6  |3.6 ±1.1  |4.3 ±0.5  |
    |disturbed by me.**          |          |          |          |          |          |
    |                            |          |          |          |          |          |
    +----------------------------+----------+----------+----------+----------+----------+
    |**It was easy to find time  |3.1 ±1.1  |2.6 ±1.2  |3.0 ±1.1  |3.0 ±1.4  |2.2 ±1.0  |
    |for training.**             |          |          |          |          |          |
    |                            |          |          |          |          |          |
    +----------------------------+----------+----------+----------+----------+----------+
    |**It was comfortable to wear|3.0 ±1.0  |2.1 ±1.0  |2.9 ±0.6  |2.7 ±1.0  |2.7 ±0.5  |
    |the headset.**              |          |          |          |          |          |
    |                            |          |          |          |          |          |
    +----------------------------+----------+----------+----------+----------+----------+


.. Note: the above data can be created when running notes/experiments/final_evaluation/data/questionaries.m




Observation and interview
-------------------------

In the process of analyzing the notes taken during the observations and the interviews, we condensed them into short sentences which were coded and categorized. From this overview, some general themes appeared which we present in this section.


First of all, none of the 4 evaluation participants experienced any technical problems using the system. At one point, we observed a training situation in which the AlphaTrainer app was not able to connect to the MindWave headset. The participant (1) immediately found out that her hair was tangled up in the power switch which had turned the headset off. She turned it on after which the app successfully connected to the headset and she continued her training. This was the closest to a technical problem we observed or heard about. This testifies to the robustness of our design and validates the technical feasibility of AlphaTrainer.


One of the themes emerging from the observation and interview notes relates to the interaction metaphors encountered in the Design Chapter |nbsp| :ref:`ch-design`. It became apparent that the participants perceive alpha training through different interaction metaphors. Especially one participant (2) who can be described as competitive in general noted that the feedbacks seemed opposite. He described that it would be more natural for him to experience greater feedback effect when his alpha level was highest, thus perceiving the feedback through the performance centered "more alpha means more feedback" metaphor. Conversely, another participant described how he felt that the Circles and Bells feedback were the most aligned with his mental model of the feedback describing his state of mind, thus perceiving the feedback through the "quiet mind (more alpha) means less feedback" metaphor.

.. -> feedback switch setting

.. - e.g. Bells stress some (Morten)
.. - depend on individuals (supported by questionnaire std.dev.)
.. - especially feedbacks on low alpha
.. -> tell people that alpha comes in chunks by nature
.. -> encourage people to use a feedback that doesn't stress them
.. -> give as soft feedback on low alpha as possible

Another theme from the observations is how the feedback in itself can have a negative effect on the relaxation and thereby on alpha performance. All participants at some point expressed that they would momentarily be interrupted from a relaxed state by the feedback. For example, one participant (4) explained that he got a shock every time a bell sound popped up as he is generally very sensitive to auditive stimuli. In most cases, however, the negative feedback effect occurred in situations where it was conveying poor alpha performance causing the participants to focus their attention on increasing alpha. As we know from the Background Chapter |nbsp| :ref:`ch-background`, this attention and state of alertness can reduce alpha activity. We suspect this to be somewhat related to the chosen metaphor behind the feedback in which the feedback is highest when alpha performance is lowest thus giving a "negative feedback". Interestingly, this negative effect was higher for certain feedbacks and it varied between the participants which feedbacks were giving this effect the most. For example, participant 2 finds the Tone stressing while participant 1 oppositely felt that the Tone was the least stressing and that the Box was most stressing feedback. The degree to which a feedback was - in their own words - "stressing" was often a reason given by the participants when stating that one feedback is better than another.




.. play an important part of the perception of a feedback.

A somehow related theme from the participant observation and interview notes is that knowledge of the nature of alpha waves is an important component in perceiving the feedback. Participant 2 explained that he experienced to get stressed when the Tone feedback increased pitch (meaning lower alpha) and that it did so in oscillations of a few seconds. We explained that alpha levels naturally follow the oscillating pattern that he had described which made him perceive the feedback very differently - he went from disliking the Tone feedback into liking it the most. For him, at least, the knowledge that high alpha activity naturally come in chunks of a few seconds made him much less stressed when he was given feedback on low alpha level by the Tone feedback. A similar experience was documented when interviewing participant 1 and the Box feedback.

.. -> introduction should include alpha knowledge

.. - in this case it was the Box feedback that was perceived to be stressing. 
.. and conversely we also experienced participants saying that know that 




Last, we present some general notions on alpha training *in situ*. Most notably, the usage of AlphaTrainer was generally very successful. The participants all found it rewarding to perform alpha training in their daily lives. This is an interesting and promising result - that the actual training practice is perceived as beneficial - since the training effect (increased alpha over time) presumably have changed very little during the week of evaluating. The participants related the alpha training practice to yoga (participant 2) and meditation (participant 3 and 4) and that AlphaTrainer fit among such de-stressing practices makes a strong argument for its feasibility.



Analysis of logged data
-----------------------

As mentioned earlier, the data logged during the evaluation is not suitable for statistical analysis due to the low sampling size, the varying feedback views and the uncontrolled environment. However, we can still look for some indications that the system performs as expected.

The first thing we look for is whether we can see higher alpha levels in the baselines recorded with closed eyes (Vibration, Tone and Bells feedbacks) than the baselines recorded with open eyes (Box and Circles feedbacks). This comparison is the closest we can get to the method we used when comparing BCIs ability to measure alpha in Chapter |nbsp| :ref:`ch-experiment`, and we expect higher alpha levels when the participants have closed eyes. That said, there are a number of factors not controlled in this comparison (e.g. the recording setup) and we can not account for the feedbacks impact on the participants ability to relax. In sum, we must be careful to not draw unsupported conclusions from the result of this comparison. To get a little more data, we decided to include the data collected during the pilot evaluation since the procedure for training did not change between the pilot and the user evaluation. The results are shown in Table |nbsp| :num:`table-logged-data-avg-alpha-baseline-open-closed-eyes-per-user`.

The results show the tendency expected, that the baselines recorded with eyes closed are generally higher than the baselines recorded with eyes open. Participant 2, however, differs for some reason consistently from this tendency. In his baselines, all recordings with open eyes are higher than the recordings with closed eyes. This could be due to a number of reasons including noise, a negative effect of the feedback stimulus or that he did not actually close his eyes eyes.

Another way of looking at the data is to order each participants baselines according to alpha level (Appendix |nbsp| :ref:`appendix-final-evaluation-ordered-baseline-recordings`). Excluding the baselines from participant 2, it only appears in 3 cases of the 24 remaining baselines that a baseline recorded with closed eyes was lower than a baseline recorded with open eyes. If AlphaTrainer was not able to detect alpha levels, we would have expected the order of the baselines to be random. The order of baselines and the general trend that baselines recorded with closed eyes are higher than baselines recorded with open eyes suggest that alpha levels are actually measured by AlphaTrainer.


.. figtable::
    :label: table-logged-data-avg-alpha-baseline-open-closed-eyes-per-user
    :caption: Average alpha of baselines per user grouped by open and closed eyes feedbacks. They are divided to get their relationship. We expect baselines under closed-eyes condition to be higher than baselines with open-eyes condition.
    :alt: Average of all alpha per baselines per user grouped by open and closed eyes feedbacks
    :spec: >{\raggedright\arraybackslash}p{0.30\linewidth} p{0.20\linewidth}  p{0.20\linewidth}  p{0.20\linewidth}
    :nofig:

    +------------------+----------------------+----------------------+----------------+
    |User              |Average baselines     |Average baselines     |Closed eyes /   |
    |                  |(open eyes)           |(closed eyes)         |open eyes       |
    +==================+======================+======================+================+
    |**Participant 1** |0.0885 (2)            |0.0941 (3)            |1.0632          |
    +------------------+----------------------+----------------------+----------------+
    |**Participant 2** |0.1202 (2)            |0.1021 (2)            |0.8488          |
    +------------------+----------------------+----------------------+----------------+
    |**Participant 3** |0.1120 (2)            |0.1143 (3)            |1.0208          |
    +------------------+----------------------+----------------------+----------------+
    |**Participant 4** |0.1041 (2)            |0.1867 (3)            |1.7933          |
    +------------------+----------------------+----------------------+----------------+
    |**Pilot 1**       |0.0885 (2)            |0.1098 (3)            |1.2406          |
    +------------------+----------------------+----------------------+----------------+
    |**Pilot 2**       |0.0720 (2)            |0.1041 (2)            |1.4469          |
    +------------------+----------------------+----------------------+----------------+


    .. Note: data is based upon a pull from the mongolab service 
    .. ~/braininterfaces/notes/experiments/final_evaluation/data/harddata_analysis_mongolab.js
    .. baselineAndFeedbackAVGalpha(feedbackIdsOpenEyes);
    .. baselineAndFeedbackAVGalpha(feedbackIdsClosedEyes);
    .. that produces some json: harddata_analysis_mongolab_result.json
    .. and added roughly to harddata_analysis_mongolab_result.m - step 1
    ..
    .. We have rechecked some of the values with in the backups of the sqlite dbs.
    ..
    .. Step 1 compare baseline open eyes versus closed eyes per person 
    .. - reproduces the experiment.

The second thing we will look for in the data is the feedback effect - the difference between the baseline and the training recordings under the same feedback. We expect alpha levels to be highest during training when the participant's alpha level control the feedback. We have calculated each relationship between a training and a baseline recording (by dividing them) - which expresses the feedback effect - and for each feedback, we have calculated the mean feedback effect per participant. Again, we have chosen to include the data from the evaluation pilot. The results are shown in Table |nbsp| :num:`table-logged-data-avg-alpha-baseline-per-user`. The number in parenthesis to the right of the feedback effect shows how many training sessions it is based on. The table also shows the average feedback effect per feedback weighted according to the number of training sessions.

Looking at the feedback effect for participant 3 and 4, they are for some reason quite consistently negative. The weighted average feedback for participant 3 is 0.90 and for participant 4 it is 0.86. Again, it is hard to comment on the reasons for this, but some reasons could be their mental strategy while training, noise (for example, person 4 mostly trained in uncomfortable backstage areas) or that they are so-called "non-responders" unable to alter their brain frequencies which according to |nbsp| :cite:p:`stopczynski_smartphones_2013` has been repeatedly reported and which excluded 26% (6 of 23) of the participants in their study. For this reason, we have calculated the weighted average feedback effect excluding participant 3 and 4.

The results show a slight general tendency of alpha levels being higher when the participants are in control of the feedback. Especially when excluding participant 3 and 4, we see a quite consistent positive feedback effect with only 3 out of 18 exceptions from the pattern that alpha levels are higher during feedback than while recording the baseline. Looking at participant 1, the feedback effect seems especially consistent across the 21 recordings she performed during the evaluation (5 baselines and 16 training sessions). The consistent pattern of alpha level being higher under feedback control (opposite but still consistent in case of participant 3 and 4) together with a clear feedback effect of participant 1 suggest that AlphaTrainer's feedback mechanism does have an effect. If there was no feedback effect, we would expect to see a more random distribution of alpha levels - especially across the participants.

We will refrain from drawing conclusions on the difference between the feedbacks due to no clear indications in the data and the small sample size. This would be very interesting to explore in a future experiment though.

.. figtable::
    :label: table-logged-data-avg-alpha-baseline-per-user
    :caption: Average of all alpha per feedback per user divided with the baseline for that specific feedback. The number of times the feedback was used per user is in (<num>). Some baselines are unfortunately not available and mark with N/A. The Pilot data is included.
    :alt: Average of all alpha per feedback per user divided with the baseline for that feedback
    :spec: l l l l l l
    :nofig:

    +-------------------+----------+----------+----------+----------+----------+
    |                   |Box       |Circles   |Vibration |Tone      |Bells     |
    +===================+==========+==========+==========+==========+==========+
    |Participant 1      |1.24 (2)  |1.11 (3)  |1.20 (4)  |1.23 (3)  |1.11 (4)  |
    |                   |          |          |          |          |          |
    +-------------------+----------+----------+----------+----------+----------+
    |Participant 2      |1.24 (2)  |0.91 (2)  |1.08 (3)  |1.02 (3)  |N/A       |
    +-------------------+----------+----------+----------+----------+----------+
    |Participant 3      |0.81 (3)  |0.83 (6)  |1.02 (4)  |0.85 (5)  |1.11 (2)  |
    +-------------------+----------+----------+----------+----------+----------+
    |Participant 4      |0.80 (4)  |1.01 (3)  |0.93 (3)  |0.86 (3)  |0.64 (2)  |
    +-------------------+----------+----------+----------+----------+----------+
    |Pilot 1            |1.25 (2)  |0.97 (1)  |0.80 (1)  |1.01 (3)  |1.10 (3)  |
    +-------------------+----------+----------+----------+----------+----------+
    |Pilot 2            |1.23 (6)  |1.23 (6)  |N/A       |1.02 (5)  |1.10 (3)  |
    +-------------------+----------+----------+----------+----------+----------+
    |**Weighted Average |1.08      |1.02      |1.05      |0.98      |1.04      |
    |all**              |          |          |          |          |          |
    +-------------------+----------+----------+----------+----------+----------+
    |**Weighted Average |1.24      |1.12      |1.11      |1.06      |1.03      |
    |all excl. 3 + 4**  |          |          |          |          |          |
    +-------------------+----------+----------+----------+----------+----------+

    .. Note: data is based upon a pull from the mongolab service 
    .. ~/braininterfaces/notes/experiments/final_evaluation/data/harddata_analysis_mongolab.js
    .. allFeedbacksPerUser();
    .. that produces some json: harddata_analysis_mongolab_result.json
    .. and added roughly to harddata_analysis_mongolab_result.m - step 3


Sum up of results
-----------------

First of all, the biggest result of the evaluation - directly addressing our thesis hypothesis - is that *it is feasible to build a system for performing alpha feedback training using a mobile device and a consumer BCI*. We base this result on these notions from the evaluation of AlphaTrainer: (*i*) the participants generally responded positively to using AlphaTrainer. The training practice was understood by the participants as a form of de-stressing practice and perceived to be immediately rewarding; (*ii*) all participants could see themselves using AlphaTrainer in the future - several of them could see them selves buying a BCI in order to use AlphaTrainer (though some would wait for the BCIs to get more discrete, comfortable and cheaper); (*iii*) the participants found it relatively easy to find the time to use AlphaTrainer; (*ii-ii*) during the evaluation, AlphaTrainer was successfully used in several situations including at home, at work and while traveling (e.g. in backstage areas); (*v*) while deployed for real world use, AlphaTrainer worked as expected without any technical problems. It was observed to handle volatility by reestablish BCI connection after an evaluation participant got the BCI's power switch tangled with her hair which turned the BCI off; additionally (*vi*) the data collected during the evaluation suggest that AlphaTrainer is able to measure the amount of alpha and that the feedback mechanism seems to positively affect the participants alpha level (in case of some participants at least).

Besides verifying our hypothesis, the evaluation has given some valuable insights to many aspects of AlphaTrainer. We now try to operationalize these insights by coming up with design changes to address the problems revealed and the ideas generated during the evaluation. The set of design revisions point towards the future work of AlphaTrainer.

- It became apparent during the evaluation that the participants perceived the feedbacks from two different metaphors, "more alpha means more feedback" and "quiet mind (more alpha) means less feedback". To support both perceptions, we suggest a user setting for reversing the highest feedback reaction from low to high alpha.

- A participant forgot to train one day. If he had not forgot, he would easily have had the time to train. We support his request for a reminder function to which could initiate a reminder notification if the user has not trained for some fixed amount of time.

- Another participant experienced many notifications - especially from emails which he receives a lot of. As a counter measure, we suggest to include some sort of in-app shortcut to turn on a quiet phone profile. An approach to this could be to rely on scripts for third party event-based applications such as On.X [#foot-evaluation-onx]_ or Tasker [#foot-evaluation-taskerm]_ which would allow a "put phone in silent mode and enable Bluetooth" script to be executed when the app launches.

- At one point during the evaluation, a participant had started training with a feedback scheduled for the day before. After changing to the feedback of the day, the AlphaTrainer app did not ask for a baseline recording since the logic only states that a baseline recording has to be performed once a day. As a result, we did not get a baseline with the feedback of that day which we missed for data analysis. Furthermore the participant did not get optimal feedback since the feedback intensity (e.g. when the Box feedback is red or green) was based on a baseline performed under a different feedback. As a countermeasure, we suggest to add the rule to the proactive interaction logic that switching feedback should always be proceeded by a baseline recording before training is allowed.

- Lastly the history view caused some confusions at times. Since alpha levels are higher when eyes are closed and the feedbacks shifted every day, the recent performances and baselines often varied very much from day to day. A way of handling this could be to only include baselines and training performances of the same feedback as the currently selected. Another way to handle this would be to subtract some sort of "closed-eyes offset" which might allow for comparisons across different feedback modalities. Whether any of these suggestions are viable solutions to the problem would of course have to be tested in a future design iteration.

Finally we conclude that the method of putting AlphaTrainer out in real world usage has been productive. Through real world usage, we have learned a lot about neurofeedback training in practice and validated the design of AlphaTrainer in a way not possible in a lab study.


.. rubric:: Footnotes

.. [#foot-evaluation-taskerm] Tasker Android app: `<https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm>`_
.. [#foot-evaluation-onx] on{X} Android app: `<https://play.google.com/store/apps/details?id=com.microsoft.onx.app>`_ 


