.. _ch-background:

============
 Background
============

In this chapter we start out briefly explaining what EEG is and how a
Brain-Computer Interface (BCI) works including typical approaches to data
processing and classical applications. We then move on to describe relevant
consumer BCIs. Finally, we outline neurofeedback training and how it relates to
stress reduction. We conclude the chapter with an overview of neurofeedback
systems which are either aimed at consumers or using consumer BCIs.


BCI / EEG
=========

The brain consists of billions of neurons. Communication between neurons is
manifested in electrical signals. Electroencephalography (EEG) measures this
electrical activity along the scalp. This is a well established technique from
the 1920s. EEG has a low spatial but a high temporal resolution which makes it
ideal for recording changes in brain activities in response to events. A BCI
takes brain activity - for example in the form of an EEG signal (which is the
case for all BCIs mentioned in this thesis) - as input |nbsp|
:cite:p:`tong_quantitative_2009`. For example, Figure |nbsp|
:num:`fig-eeg-with-alpha-waves` shows an EEG signal with visible alpha waves.

.. _fig-eeg-with-alpha-waves:

.. figure:: fig/eeg_wave_with_alpha.png
    :alt: EEG with alpha waves
    :width: 100%
    :align: center
    
    EEG signal with alpha waves marked with black boxes.


Brain activity is not the only source of electrical signals along the
scalp. Muscle activation also relies on electrical signals, the measuring of
which is called electromyography (EMG). Eye movement furthermore discharges
electricity due to the eyes dipole properties - measuring this signal is called
electrooculography (EOG). In the context of measuring EEG, EMG and EOG are
typical noise artifacts |nbsp| :cite:p:`majumdar_human_2011`.

EEG is measured either with stand-alone electrodes or electrodes attached to a
cap. Examples of high fidelity EEG BCIs are the *gamma-2-cap* from *g.tec*
[#foot-background-gtec]_ and *Easy Cap* from EASYCAP
[#foot-background-easycap]_. Some caps can even have up to 256 electrodes
mounted |nbsp| :cite:p:`tong_quantitative_2009`. Caps need mounting preparations
with gel to improve the conductivity between scalp and electrodes. We have tried
out the *gamma-2-cap* during a BCI seminar in Aalborg 2013 (Figure |nbsp|
:num:`fig-bci-classic-cap-martin-pelle`). A hi-fi EEG based BCI cost around
10-15.000 Euro and includes, for example, a cap with electrodes, cables
and an amplifier.

The EEG data is usually processed and analyzed off line with tools like EEG-lab
|nbsp| :cite:p:`delorme_eeglab:_2004` or FieldTrip |nbsp|
:cite:p:`oostenveld_fieldtrip:_2011` which are open-source plug-ins to MATLAB
|nbsp| [#foot-background-matlab]_.

.. _fig-bci-classic-cap-martin-pelle:

.. figure:: fig/gcap2_martin_pelle_collage.png 
    :alt: Gamma-2-cap
    :width: 70%
    :align: center
    
    Martin and Pelle wearing a gamma-2-cap mounted by Gunther Krausz from g.tec


Classic BCI applications and techniques
---------------------------------------

There are different approaches to processing a raw EEG signal. Some of these and
their typical applications are briefly covered below.

Evoked Potentials correlates visual/auditory stimuli with EEG responses. When an
event of significance is perceived, the brain fires certain action
responses. One widely used response is the P300 which manifests itself as a peak
in the EEG signal 300 ms after a stimulus - for example a flash of an image. In
the *intendiX* [#foot-background-intendix]_ P300 speller application from
*g.tec* different letters are flashed for user while the P300 action response is
used to determine which letter the user wants to select.

Motor imagery is another classic approach to BCI in which an imagined movement
of a body part causes motor cortex activity which is detected by the BCI. In
this way imagined movement can be used for example to control wheel chairs and
other vehicles |nbsp| :cite:p:`mcfarland_brain-computer_2011`. This technique
has been used in gaming as well, e.g. for trigger activation |nbsp|
:cite:p:`coyle_eeg-based_2011`. Motor imagery requires spatialization
(localization) of brain activity especially within motor cortex. This
presents a challenge for EEG based BCIs since they have a low spatial
resolution.

Classification of EEG signals are widely used within BCI applications. For
example, it has been used for unique identification of a person for
authentication purpose |nbsp| :cite:p:`schmalstieg_gaze-directed_2010`. Various
research groups uses classifications to predict epilepsy attacks |nbsp|
:cite:p:`stam_nonlinear_2005` :cite:p:`meng_feature_2010`. Others do pattern
matching on walking motions for assisting in rehabilitation after strokes
:cite:p:`kuramoto_trigger_2012`. This approach has also been used to classify:
(*i*) emotions like joy and anger; and (*ii*) human expressions like a happy
facial expression or a mental mood |nbsp| :cite:p:`hutchison_emotional_2011`
:cite:p:`bekkedal_human_2011` :cite:p:`ichi_ito_association_2010`.

.. subfigstart::

.. _fig-background-mindwave_eeg_raw:

.. figure:: fig/mindwave_eeg_raw.png
    :alt: Single channel raw EEG
    :width: 100%
    :align: center
    
    Single channel raw EEG with 512 samples per second.

.. _fig-background-mindwave_eeg_fft:

.. figure:: fig/mindwave_eeg_fft.png
    :alt: Single channel raw EEG applied FFT
    :width: 100%
    :align: center
    
    Single channel EEG after Fast Fourier transform (FFT) has been applied.

.. subfigend::
    :width: 0.48
    :alt: Raw EEG and processed EEG
    :label: fig-background-eeg-raw-fft
    
    Raw EEG and Fast Fourier transformed EEG.


Frequency analysis is another technique for processing EEG data.
Neurons are organized in networks and communication among them is always ongoing
in oscillatory patterns. Frequency analysis estimates the power of each
frequency component. One common approach to frequency analysis is to apply Fast
Fourier transform (FFT) - a simple example is plotted in Figure |nbsp|
:num:`fig-background-eeg-raw-fft`. When applying FFT we go from a time domain
into a frequency domain as can be seen on the x-axis values of the plots before
and after FFT. Frequency analysis is often used in conjunction with
other methods of analysis - for example to extract features for classification
|nbsp| :cite:p:`tong_quantitative_2009`. It is also used stand-alone either for
neurofeedback or in research aiming to correlate certain frequency patterns with
some condition or cognitive task. This is very typical within EEG research
exemplified by a study showing that "*... high resting theta power in healthy
older adults is associated with better cognitive function*" |nbsp|
:cite:p:`finnigan_resting_2011`.

Frequency analysis is interesting due to the correlation between frequencies and
mental states |nbsp| :cite:p:`hammond_what_2007` |nbsp|
:cite:p:`rangaswamy_beta_2002`. A rough overview is lined up in Table |nbsp|
:num:`table-background-frequency-bands`.

.. figtable::
    :label: table-background-frequency-bands
    :caption: Generalized frequency bands
    :alt: Generalized frequency bands
    :spec: l l l
    :nofig:

    +---------------+----------------+------------------------------------------------+
    |Brainwave Type |Frequency range |Mental states and conditions                    |
    +===============+================+================================================+
    |**Delta**      |0.5Hz to 3.5Hz  |Deep sleep                                      |
    |               |                |                                                |
    +---------------+----------------+------------------------------------------------+
    |**Theta**      |3.5Hz to 8Hz    |Falling asleep                                  |
    |               |                |                                                |
    +---------------+----------------+------------------------------------------------+
    |**Alpha**      |8Hz to 12Hz     |Relaxed awake state (dominant with eyes closed) |
    |               |                |                                                |
    +---------------+----------------+------------------------------------------------+
    |**Beta**       |12Hz to 30Hz    |Mental activity, attention, concentration       |
    |               |                |                                                |
    +---------------+----------------+------------------------------------------------+
    |**Midrange     |16Hz to 20Hz    |Thinking, aware of self & surroundings          |
    |Beta**         |                |                                                |
    +---------------+----------------+------------------------------------------------+
    |**High Beta**  |21Hz to 30Hz    |Alertness, agitation                            |
    |               |                |                                                |
    +---------------+----------------+------------------------------------------------+
    |**Gamma**      |30Hz to 100Hz   |Reflects the mechanism of consciousness         |
    |               |                |                                                |
    +---------------+----------------+------------------------------------------------+


The hi-fi BCIs are getting mobile. This trend is exemplified by a mobile version
of the *Easy Cap* and helmets with built in EEG sensors for soldiers |nbsp|
:cite:p:`matthews_real_2008`. Another branch of BCIs that have come far in
getting mobile are the consumer BCIs as described in the next section.


.. _ch-background-consumer-bcis:

Consumer BCIs
=============

Within recent years consumer BCIs have emerged and moved BCIs outside the
laboratories. An early consumer BCI was the Neural Impulse Actuator (NIA)
|nbsp| [#foot-background-nia]_ released in 2008 featuring a three forehead sensor
configuration and connectivity through a desktop box with cables. NIA was
intended primarily for gaming and cost around 100 USD (it is not in production
any longer). Consumer headsets today typically offer additional sensors
(accelerometer, gyroscope, etc) and wireless connectivity.  An overview of
current state consumer BCIs is presented in Table |nbsp|
:num:`table-consumer-bcis`.

.. note: is the mindset from 2007 or 2009: 
.. according to https://en.wikipedia.org/wiki/Comparison_of_consumer_brain%E2%80%93computer_interfaces its from 2007
.. but according http://developer.neurosky.com/docs/lib/exe/fetch.php?media=mindset_instruction_manual.pdf
.. and http://en.wikipedia.org/wiki/NeuroSky its from 2009 which means nia seems to be the first...
.. NIECETOHAVE: perhaps ask at forum and or adjust the wikipedia entry


.. figtable::
    :label: table-consumer-bcis
    :caption: Listing of consumer BCIs compared by selected features.
    :alt: Listing of consumer BCIs compared by selected features
    :spec: >{\raggedright\arraybackslash}p{0.18\linewidth} p{0.14\linewidth} p{0.14\linewidth} p{0.14\linewidth} p{0.14\linewidth} p{0.14\linewidth} 
    :nofig:
             
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+
    |Feature                 |Emotiv EPOC (Research) |MindWave Mobile       |TrueSense Kit (OPI) |Muse                |Emotiv INSIGHT         |
    |                        |                       |                      |                    |                    |                       |
    |                        |                       |                      |                    |                    |                       |
    +========================+=======================+======================+====================+====================+=======================+
    |**Raw EEG**             |No / Yes               |Yes                   |Yes                 |Yes                 |Yes                    |
    |                        |                       |                      |                    |                    |                       |
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+
    |**Electrodes**          |14                     |1                     |2                   |4                   |5                      |
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+
    |**Locations**           |AF3, F7, F3, FC5, T7,  |--                    |--                  |AF3, AF4, TP9, TP10 |AF3, AF4, T7, T8, Pz   |
    |                        |P7, O1, O2, P8, T8,    |                      |                    |                    |                       |
    |                        |FC6, F4, F8, AF4       |                      |                    |                    |                       |
    |                        |                       |                      |                    |                    |                       |
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+
    |**Sensors type**        |Wet                    |Dry                   |Dry/gel             |Dry                 |Dry                    |
    |                        |                       |                      |                    |                    |                       |
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+
    |**Sampling rates**      |128Hz                  |512Hz                 |512Hz               |100-600Hz           |128Hz                  |
    |                        |                       |                      |                    |                    |                       |
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+
    |**Protocol**            |USB Dongle             |Bluetooth             |ZigBee              |Bluetooth           |Bluetooth              |
    |                        |                       |                      |                    |                    |                       |
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+
    |**Power**               |12 hours               |6-8 hours (AAA bat.)  |18 hours            |10 hours            |4 hours                |
    |                        |                       |                      |                    |                    |                       |
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+
    |**Off Line recording**  |N/A                    |N/A                   |Memory chip         |N/A                 |microSD card           |
    |                        |                       |                      |                    |                    |                       |
    |                        |                       |                      |                    |                    |                       |
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+
    |**Extra Sensors**       |Gyroscope              |None                  |Accelerometer,      |Accelerometer       |Accelerometer,         |
    |                        |                       |                      |temperature         |                    |magnetometer           |
    |                        |                       |                      |                    |                    |                       |
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+
    |**SDK**                 |OSX, Windows           |Android, IOS, Windows,|Linux, Windows, OSX |Android, IOS, Linux,|Android, IOS, Linux,   |
    |                        |                       |OSX                   |                    |Windows, OSX        |Windows, OSX           |
    |                        |                       |                      |                    |                    |                       |
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+
    |**Price**               |300/750 USD            |100 EURO              |40 EURO             |269 EURO            |300 USD                |
    |                        |                       |                      |                    |                    |                       |
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+
    |**Released**            |2009                   |2011                  |2013                |Ann. 2014           | Ann. 2014             |
    +------------------------+-----------------------+----------------------+--------------------+--------------------+-----------------------+



These headsets are interesting to our project. Relevant features and how they
have been used in research is lined out in the next sections.


.. subfigstart::

.. _fig-background-consumer-bcis-epoc:

.. figure:: img/bci-emotiv-epoc.jpg
    :alt: Emotiv EPOC
    :width: 100%
    :align: center
    
    Emotiv EPOC. The image show USB Dongle, electrodes and the EPOC headset 


.. _fig-background-consumer-bcis-mindwave:

.. figure:: img/bci-neurosky-mindwave-mobile.jpg
    :alt: NeuroSky MindWave Mobile
    :width: 100%
    :align: center
    
    NeuroSky MindWave Mobile headset.


.. _fig-background-consumer-bcis-truesense:

.. figure:: img/bci-truesense-kit.jpg
    :alt: TrueSense Kit
    :width: 100%
    :align: center
    
    TrueSense Kit. The image show USB controller (w. ZigBee receiver), memory module and TrueSense sensor band. 


.. subfigend::
    :width: 0.45
    :alt: Images of consumer BCIs
    :label: fig-background-consumer-bcis-images
    
    Images of 3 consumer BCIs.


.. _ch-background-epoc:

Emotiv EPOC
-----------

EPOC has out of the box a desktop SDK and a set of tools aimed at gaming. The
closed source SDK provides detection of emotions, expressions, cognitive states
and more |nbsp| [#foot-background-emotiv]_ (Figure |nbsp|
:num:`fig-background-consumer-bcis-epoc`).

There is also a research edition of the EPOC headset which can record raw
EEG. It comes with the *TestBench* desktop application for
recording and viewing the raw EEG data. TestBench can process EEG into
various frequency bands and the raw EEG data can be exported in an EDF-format
(multichannel biological and physical signals) [#foot-background-edf]_ (Appendix
|nbsp| :ref:`appendix_background_testbench`).

Before using the EPOC headset, the user has to moist each of its 14 electrode in
a saline solution and then attach each electrode to the headset. This
preparation took us about 10-15 minutes when some routine was achieved.

The EPOC has no SDK for mobile devices, but has been hacked for mobile usage in
conjunction with the USB dongle - we return to this in Section |nbsp|
:ref:`sec_related_works`.

EPOC seems to be the consumer BCI that appears most frequently in research
papers. An overview of its application within research is given below.

The *FlyingBuddy2* uses motor imagery to make it possible for a disabled person
to steer a Drone with the future perspective of steering a wheel chair |nbsp|
:cite:p:`yu_flyingbuddy2:_2012`. A group in Spain uses the out of the box SDK
classified facial expression (based on EMG) such as open and close clinch
combined with EOG data to steer a tractor |nbsp|
:cite:p:`gomez-gil_steering_2011`. Again using SDK classifications, an emotion
based chat application has been build featuring avatars that changes their
expression from angry to happy based on the emotional state of a person |nbsp|
:cite:p:`wright_emochat_2010`. In a recent M.Sc. thesis the EPOC was used for a
brain wave biometrics authentication system |nbsp|
:cite:p:`petersen_development_2012`. The *NeuroPhone* project used a P300
approach to make phone calls on a smart phone - however the EEG processing was
performed on a laptop |nbsp| :cite:p:`campbell_neurophone:_2010`. Finally, EPOC
has also been used in a human-robot interaction study where they used EEG to
classify human satisfaction of the interaction with a robot |nbsp|
:cite:p:`esfahani_using_2011`.

EPOC has also been used by media researchers at the Danish
Broadcasting Corporation (DR) as a supplemental tool to qualitative interviews
and questionnaires. Throughout the video screening of a TV Drama production,
the screening participants' brain states were measured in terms of EPOC SDK
values such as excitement, frustration and attention. In an
interview with Harddisken (a DR radio program about technology), Jacob Lyng
Wieland - in charge of the experimental usage of BCI during video screenings -
reported that they had skipped using the EPOC headset because it was too
cumbersome to use |nbsp| [#foot-background-harddisk]_.


.. _ch-background-mindwave:

NeuroSky MindWave Mobile
------------------------

NeuroSky MindWave Mobile (MindWave) |nbsp| [#foot-background-mindwave]_ offers
desktop and mobile SDKs (IOS and Android). The closed source SDK features
frequencies processing and analysis outputting values for the level of
"attention" and "meditation" |nbsp| :cite:p:`neurosky_brain_2009` (Figure |nbsp|
:num:`fig-background-consumer-bcis-mindwave`). The SDK also provides information
about eye blinks and a number of frequency bands which we previously have lined
out in Figure |nbsp| :num:`table-background-frequency-bands`. The
MindWave SDK outputs the following frequency bands: delta (0.5 - 2.75Hz), theta (3.5 - 6.75Hz),
low-alpha (7.5 - 9.25Hz), high-alpha (10 - 11.75Hz), low-beta (13 - 16.75Hz),
high-beta (18 - 29.75Hz), low-gamma (31 - 39.75Hz) and mid-gamma (41 - 49.75Hz)
|nbsp| :cite:p:`neurosky_thinkgear_2012`.

The headset is easy to use and the SDK includes a simple Bluetooth API that
seamlessly supports device connectivity. Due to its connectivity options and SDK
signal processing, the MindWave Mobile requires little effort to embed in a
prototype. This has been done, for example, in a recent paper by Marchesi.
He uses MindWave in the
BRAVO project to detect attention among school children in an e-learning
setting. If a child's attention level is under some threshold, it its reported
to the other children who are encouraged to offer their help |nbsp|
:cite:p:`marchesi_bravo:_2013`. In another study, a research group uses
MindWave to measure
attention during an online game. They specifically look at the attention
levels provided by the SDK versus self reported attention levels among a group of
participants. They conclude that the self reports and the SDK values are correlated |nbsp|
:cite:p:`hutchison_assessing_2009`. Another paper uses the attention and
meditation SDK values to examine the stress levels among participants while
performing various tasks. It concluded that the
MindSet [#foot-background-mindset]_ was able to measure an increase in stress
induced by the tasks performed (Stroop test, Tower of Hanoi) |nbsp|
:cite:p:`crowley_evaluating_2010`.
In |nbsp|
:cite:p:`yasui_brainwave_2009`
the brain state - defined in terms
of EEG frequency composition - of a test subject driving a car is measured by
a predecessor to the MindWave. Raw EEG data is recorded to a mobile phone via
bluetooth and its frequency composition is analyzed offline.
Interestingly, the results show a change in the brain wave frequency pattern
when the driver performed, for example, a phone call.
Finally, in a M.Sc. thesis, classification of the raw EEG data from the MindSet
is used to control a snake-like game aimed at children |nbsp|
:cite:p:`larsen_classification_2011`.

MindWave comes out of the box with a mobile application named *Brainwave
Visualizer* which let its user inspect the current levels of the 8 frequency
bands supported by the SDK. The app also provides simple neurofeedback by
letting its user control the flying height of a ball by the SDK "meditation"
value or the intensity of a flame by the SDK "attention" value. The same
approach to neurofeedback is used in the third party app *Transcend* by Personal
Neuro. During meditation the user can get a flower to grow by increasing the
"meditation" SDK value |nbsp| [#foot-background-transcend]_.


.. _ch-background-truesense-kit:

TrueSense Kit
-------------

TrueSense Kit is the newest, cheapest, most portable headset. It comes with OPI
Console, an open source desktop application for recording and viewing raw EEG
data and analyzing sleep, meditation etc. from recorded EEG. It also enables exporting data as
EDF-files for further processing and analysis in other applications. The OPI
Console also offers sleep analysis and yoga performance analysis |nbsp|
[#foot-background-opi]_ (Figure |nbsp|
:num:`fig-background-consumer-bcis-truesense`, Appendix |nbsp|
:ref:`appendix_background_truesense_console`). The TrueSense Kit sensor(s) can
be placed on various parts of the body for measuring blood flow, heart rate, body
temperature and body movements.

TrueSense Kit records either directly to an internal memory module or transmit
data over ZigBee radio to the OPI Console through a USB receiver. The sensors
can be combined in a multi sensor configuration attached various places on the
head or body.

TrueSense Kit provides no immediate mobile device connectivity but the OPI Console
application can likely be ported to Android since it is build with the QT
framework |nbsp| [#foot-background-qt]_. Another approach would be to build a
native C++ Android module from the TrueSense Kit C++ SDK. Since few Android
devices currently support ZigBee out of the box, this would require an
external receiver board.

TrueSense Kit is not yet covered in any papers despite its support for flexible
experimental setups. TrueSense Kit was warmly received by the quantified self
community at the yearly QS conference in Amsterdam 2013 |nbsp|
[#foot-background-quantified-2013]_.


.. _ch-background-future-headsets:

Future headsets
---------------

New consumer BCIs are about to arrive, for example *Muse* |nbsp|
[#foot-background-muse]_ (as briefly mentioned in the Introduction Section
|nbsp| :ref:`ch-intro-neurofeedback-stress-and-bci`) and *Emotiv INSIGHT* |nbsp|
[#foot-background-insight]_. These new headsets have some characteristics in
common which seem to be representative for the new generation of consumer BCIs:

- they support Bluetooth
- they use dry electrodes
- they are discrete and comfortable to wear

An interesting fact is that both of these headbands are
crowdfunded. Muse raised 287,472 USD in 2012 from an unknown amount of
supporters at Indiegogo |nbsp| [#foot-background-indiegogo]_. EPOC Insight had
pledged 1,643,117 USD by the end of September 2013 from nearly 5000 people on
Kickstarter |nbsp| [#foot-background-kickstarter]_. This trends an interest in
low cost consumer BCIs and exemplifies pretotyping by presenting and selling the
product before it has actually been build |nbsp|
:cite:p:`jeremy_pretotypingwork_2012`.

Most importantly, these new BCIs strengthen the possibility for neurofeedback
among consumers in their daily settings. In the next section we focus on the
neurofeedback concept.



Neurofeedback
=============

When given real time feedback on its oscillations, the brain can learn to
control and change them. This is interesting since the brains oscillations are
significantly correlated with brain functions and behavior as well as with
psychiatric diseases |nbsp| :cite:p:`zoefel_neurofeedback_2011`. Neurofeedback
training exploits this mechanism by providing feedback based on oscillation
frequencies correlated with some desirable function or behavior.

The neurofeedback mechanism was discovered and developed in the 1960s, but the
first controlled studies providing clinical evidence supporting neurofeedback
training effects were published in the 1980s |nbsp|
:cite:p:`angelakis_eeg_2007`. Since then, the efficacy of neurofeedback therapy
has been documented in several studies |nbsp| :cite:p:`lofthouse_review_2012`
|nbsp| :cite:p:`arns_efficacy_2009` |nbsp| :cite:p:`white_alphatheta_2009` and
neurofeedback [#foot-aap]_ is listed among the treatments with highest evidence
support for certain conditions according to The American Academy of Pediatrics
(AAP) |nbsp| :cite:p:`_aap_2013`. Neurofeedback is routinely used in
treatment of a number of conditions including Attention Deficit Hyperactivity
Disorder (ADHD), anxiety, epilepsy, and addictive disorders |nbsp|
:cite:p:`angelakis_eeg_2007`.

Besides its clinical usage, a number of studies show that neurofeedback training
can increase cognitive performance. For example, it has been shown to increase
semantic working memory,
focused attention, perceptual sensitivity and reaction time |nbsp|
:cite:p:`angelakis_eeg_2007`. Neurofeedback training has also been shown
effective by real-life behavioral measures - e.g. by increasing musical
performance in a stressful context among conservatory students in a study
designed to ensure ecological validity |nbsp|
:cite:p:`egner_ecological_2003`.


Neurofeedback in practice
-------------------------

In a typical clinical context, neurofeedback sessions of 45-60 minutes duration
are performed twice per week. The number of treatments depend on the individual
response to the training and the condition being treated - e.g. 40-80 sessions
are suggested in ADHD treatment |nbsp| :cite:p:`angelakis_eeg_2007`.

Neurofeedback therapy is relatively expensive. For example, 40 training sessions
cost > DKR 30.000,- at Ann-Helen Pettersen's clinic |nbsp| [#foot-background-hjernetraening]_.


.. _sec-background-stress-alpha-feedback-training:

Stress and alpha feedback training
----------------------------------

Alpha feedback training is the subset of neurofeedback training for
which the goal state of the feedback is defined in terms of the amount
of alpha waves - thereby seeking to increase the alpha activity.

Alpha activity is associated with a relaxed consciousness |nbsp|
:cite:p:`angelakis_eeg_2007`. Together with theta, alpha is the EEG
frequency band in which effects of meditation are most significant
|nbsp| :cite:p:`aftanas_changes_2003` |nbsp|
:cite:p:`brandmeyer_meditation_2013`. Alpha 'blocking' (i.e.,
reduction) is associated with alertness |nbsp|
:cite:p:`angelakis_eeg_2007`. Thus, by increasing alpha levels, alpha
feedback training has been shown - amongst other positive effects such
as increased cognitive performance - to reduce stress and anxiety
|nbsp| :cite:p:`zoefel_neurofeedback_2011` |nbsp|
:cite:p:`angelakis_eeg_2007` |nbsp| :cite:p:`white_alphatheta_2009`.

With a classification approach, EEG has been used to classify subjects
from either a chronically stressed or a control group with a success
rate higher than 90% |nbsp| :cite:p:`khosrowabadi_brain-computer_2011`. This
testifies to the manifestation of stress in EEG data.



The dominant frequency within the alpha band - the *alpha peak* - and the
amplitude of the alpha band varies between individuals |nbsp|
:cite:p:`bazanova_comments_2012` |nbsp| :cite:p:`angelakis_eeg_2007`
|nbsp| :cite:p:`zoefel_neurofeedback_2011`. An alpha feedback training
system can account for this by calibrating according
to the individual alpha peak and the baseline amount of alpha. This is,
for example, the approach taken in the alpha feedback system presented in
|nbsp| :cite:p:`stopczynski_smartphones_2013`. The importance of giving
feedback on individually determined frequency bands is investigated in |nbsp|
:cite:p:`bazanova_comments_2012`
and concludes that
"*Neurofeedback training
applied in individual EEG frequency ranges was much
more efficient than neurofeedback training of standard
EEG frequency ranges*".


.. _sec_related_works:

Related works
=============

Having explained current state of consumer EEG BCIs, the neurofeedback mechanism
and how alpha feedback training can help to reduce stress, we now present
existing systems and research within the consumer neurofeedback domain. There is
only a limited number of such systems and research for reasons already mentioned
above:

1. Neurofeedback therapy is expanding but not widely adopted yet.
2. Consumer BCIs have only emerged within recent years. They are still maturing and not
   widely adopted yet.

This section present and discuss the commercially available systems
Brainball and BioZen and the research project SmartphoneBrainScanner2.


.. _ch-background-brain-ball:

Brainball
---------

.. - neurofeedback (QEEG similar to ours)
.. - headset similar to NIA
.. - tangible interface
.. - niche entertainment gaming product

According to the researchers behind, Brainball "*... dwells in the realm between
art and research, entertainment and science, method and object*" |nbsp|
:cite:p:`hjelm_research+_2003`. They present a game with a tangible user
interface in which two opponents sit on a chair separated by a table. A steel
ball lies between them. The players wear specialized BCIs
mounted on their foreheads and somewhat similar to the NIA system (see Section
:ref:`ch-background-consumer-bcis`).
The EEG signal is analyzed into its frequency components and the ball
will roll away from the most relaxed player (drawing on the correlation between
alpha activity and relaxation). While playing, the players are able to see a
screen visualizing their EEG activity. The creators of Brainball interestingly
reports that playing the game leads to increased relaxation by measure of both
Galvanic Skin Response (GSR) and self reports
:cite:p:`hjelm_research+_2003`. Brainball experienced a lot of attention
including honorary mention at Ars Electronica 2000 and 100+ appearances on
TV. However, it remains a niche product within gaming and entertainment due to
the dependency on specialized hardware (BCI, ball, screen, etc). The
Brainball BCI system is commercially available through a Swedish
company under the name *Mindball* [#foot-background-mindball]_ (Figure |nbsp|
:num:`fig-bci-related-mindball-game`).


.. _fig-bci-related-mindball-game:

.. figure:: fig/mindball-game.jpg
    :alt: Mindball game
    :width: 80%
    :align: center
    
    Brainball BCI system in the new version named Mindball. A 
    monitor displays the brain activity of the participants (Image courtesy of 
    Interactive Productline IP AB).


.. _ch-background-bio-zen:

BioZen
------

BioZen |nbsp| [#foot-background-biozen]_ is a consumer biofeedback system
developed by the National Center for Telehealth and Technology (T2) under the US
Department of Defense. The fact alone that this organization is behind a
biofeedback system witnesses to the increasing adoptation of the biofeedback
(here under neurofeedback) method. The system consists of an Android application
|nbsp| [#foot-background-biozen-app]_ in conjunction with one or more consumer
bio-sensors. Several sensors are supported including heart rate, skin
temperature, GSR and EEG sensors. For EEG measurements, the Neurosky MindWave
(and some older Neurosky BCIs) are supported. The BioZen app uses processed data
delivered from the Neurosky SDK (Delta, Theta, Low Alpha, High Alpha, Low Beta,
High Beta, Low Gamma, Mid Gamma, (e)Attention, (e)Meditation) and these values
can form the basis for neurofeedback training. Relying on the Neurosky SDK for
frequency analysis, BioZen is bound to the limited set of frequency spectra
mentioned above.

On the BioZen web page, T2 claims that "*BioZen is the first portable, low-cost
method for clinicians and patients to use biofeedback in and out of the clinic*"
and that "*[BioZen] takes many of the large medical sensors in a clinic and puts
them in the hands of anyone with a smart phone*" |nbsp|
[#foot-background-biozen]_. In other words, it is promoted for clinical usage -
a claim the authors of this thesis are very cautious about making on behalf of
AlphaTrainer (see Section :ref:`ch-intro-limitations`).


.. subfigstart::

.. _fig-background-biozen-feedback:

.. figure:: img/biozen_feedback.png
    :alt: BioZen feedback
    :width: 80%
    :align: center
    
    BioZen feedback consisting of a sun varying from dark (low alpha) to light (high alpha). 
    A new age soundtrack loops in the background (can be 
    disabled in the configuration).


.. _fig-background-biozen-feedback-gain-control:

.. figure:: img/biozen_feedback_gain_control.png
    :alt: Gain alpha.
    :width: 80%
    :align: center
    
    The input gain of the feedback parameter (i.e. the alpha band) can be adjusted through a slider thus providing a manual calibration.


.. _fig-background-biozen-feedback-save:

.. figure:: img/biozen_feedback_save.png
    :alt: Save feedback session.
    :width: 80%
    :align: center
    
    Save feedback session with a tag (meditation, breathing, entertainment or 
    working) and a note.

.. subfigend::
    :width: 0.30
    :alt: Screen shoots of the neurofeedback from the BioZen Android app using the MindWave BCI
    :label: fig-background-biozen-app-feedback
    
    Screenshots of the neurofeedback from the BioZen Android app using 
    the MindWave BCI (Images courtesy of BioZen).


The feedback consists of an image of a hill in which the background brightness
and the visibility of a foreground tree are the feedback variables. The
background is brighter when the chosen parameter (e.g. some EEG power band) is
higher while the foreground tree is more visible when the chosen parameter is
more stable |nbsp| :cite:p:`t2_biozenusersman_1_7_0.pdf_2013` (see Figure |nbsp|
:num:`fig-background-biozen-app-feedback`).



.. _ch-background-smartphone-brain-scanner-2:

Smartphone Brain Scanner 2
--------------------------

The Smartphone Brain Scanner is developed at the Technical University of Denmark
(DTU). The project aims at moving EEG research out of the laboratory by means of
low cost wireless BCIs and smart phone based real-time neuroimaging software
which "*may transform neuroscience experimental paradigms*" |nbsp|
:cite:p:`stopczynski_smartphones_2013`. The important notion here is that while
leaving the laboratory and using consumer interfaces, the focus is still on
research.

They are in principle headset agnostic and support the *Easy Cap* and EPOC (described in Section :ref:`ch-background-epoc`)
BCIs. The EPOC is both used in its standard configuration and in a modified
configuration in which it is merged with hi-fi gel based electrodes. On the
software side, they use their Smartphone Brain Scanner (SBS2) open source
software framework including state of the art EEG signal processing such as
source reconstruction, noise filtering and frequency analysis |nbsp|
[#foot-background-smartphonebrainscanner]_. It is build on the QT C++ framework
|nbsp| [#foot-background-qt]_ which allows compilation to the major desktop and
mobile operating systems. However, it is not trivial to embed a QT module inside
another native applications e.g. on the Android platform. Wireless connection to
the EPOC BCI goes via an USB dongle and requires an Android phone to be rooted
to function, the platform does not provide an easy way of interfacing with BCIs
via bluetooth. Furthermore it requires the research edition of the EPOC.

To validate the design of the Smartphone Brain Scanner, the research team behind
has build 3 brain imaging applications including an alpha training
application. Again, the focus is on research - specifically, the interface
parameters of neurofeedback training are investigated. The efficacy of two
different feedbacks were compared in a controlled study by measuring increase in
alpha amplitudes with each interface during a week of intensive training. One
feedback show a square changing colors between blue over gray to red for which
red represents high alpha. In another interface, high alpha amplitudes manifests
itself in the creation of small boxes and the color of the boxes created. By
keeping the created boxes visible during the 5 minute training period, the
interface reveals performance history thus "*allowing the user to easily compare
methods for increasing the amplitudes*" |nbsp|
:cite:p:`stopczynski_smartphones_2013` (Figure |nbsp|
:num:`fig-related-smartphone-brain-scanner-feedback`). The training effect
measured by comparing baselines revealed only a statistic significant increase
in alpha for the box changing colors while the alpha levels during training were
significantly higher using the square creation interface.

The conclusions especially relevant to this thesis are that:

1. Alpha feedback training is feasible in a mobile setup.

2. Alpha levels during training (effect of feedback) is not necessarily
   correlated with a general increase in alpha levels (effect of training).

.. _fig-related-smartphone-brain-scanner-feedback:

.. figure:: fig/smartphone-brain-scanner-feedback.png
    :alt: Smartphone Brain Scanner neurofeedback interface
    :width: 60%
    :align: center
    
    Smartphone Brain Scanner neurofeedback interface. High alpha amplitudes manifests
    itself in the creation of small boxes and their color. By
    keeping the created boxes visible during the 5 minute training period, the
    interface reveals performance history |nbsp| :cite:p:`stopczynski_smartphones_2013`.
    Image courtesy of the Smartphone Brain Scanner project.


Sum up of background and related systems
========================================

Table |nbsp| :num:`table-related-systems` lists neurofeedback systems
which are either commercially available or use a consumer BCI.
These systems have been chosen because they
outline the current state of systems in the domain of AlphaTrainer.
The parameters highlighted in the table express
parameters desirable or necessary for a consumer neurofeedback system.
No existing system includes all parameters. For example,
no consumer available system includes the ability to give feedback on individually
adapted frequency bands which is important for the effectiveness of
the feedback training (see Section |nbsp|
:ref:`sec-background-stress-alpha-feedback-training`).
This "gap" among current neurofeedback systems is our motivation
for designing and building
AlphaTrainer as discussed in the following chapters.


.. figtable::
    :label: table-related-systems
    :caption: Related systems
    :alt: Related systems
    :spec: >{\raggedright\arraybackslash}p{0.20\linewidth} p{0.20\linewidth} p{0.10\linewidth} p{0.10\linewidth}  p{0.20\linewidth}
    :nofig:

    +-----------------------------+-----------------------+------------+------------+-------------------------+
    |Parameters                   |Brainwave Visualizer & |Brianball   |BioZen      |Alpha feedback app -     |
    |                             |Transcend              |            |            |Smartphone Brain Scanner |
    +=============================+=======================+============+============+=========================+
    |**Convenient (dry sensor +   |yes                    |no          |yes         |no                       |
    |bluetooth connectivity)**.   |                       |            |            |                         |
    +-----------------------------+-----------------------+------------+------------+-------------------------+
    |**Headset agnostic**.        |no                     |no          |yes         |(yes)                    |
    +-----------------------------+-----------------------+------------+------------+-------------------------+
    |**Individual feedback.       |no                     |n/a         |no          |yes                      |
    |spectra**                    |                       |            |            |                         |
    +-----------------------------+-----------------------+------------+------------+-------------------------+
    |**Efficacy documented**.     |no                     |no          |no          |yes                      |
    +-----------------------------+-----------------------+------------+------------+-------------------------+
    |**Available to customers**.  |yes                    |yes         |yes         |no                       |
    +-----------------------------+-----------------------+------------+------------+-------------------------+
    |**Low cost**.                |yes                    |no          |yes         |n/a                      |
    +-----------------------------+-----------------------+------------+------------+-------------------------+



.. rubric:: Footnotes

.. [#foot-background-gtec] `<http://www.gtec.at>`_

.. [#foot-background-easycap] `<http://www.easycap.de/easycap>`_

.. [#foot-background-matlab] `<http://www.mathworks.se/products/matlab>`_

.. [#foot-background-intendix] `<http://www.gtec.at/Products/Complete-Solutions/intendiX-Specs-Features>`_

.. [#foot-background-hjernetraening] `<http://www.hjernetraening.dk/prisliste.html>`_

.. [#foot-background-emotiv] `<http://emotiv.com>`_

.. [#foot-background-edf] `<http://www.edfplus.info>`_

.. [#foot-background-harddisk] `<http://www.dr.dk/radio/player/ondemand/legacybyrid/1588020#!>`_

.. [#foot-background-nia] `<http://ocz.com/consumer/company/newsroom/news/ocz-announces-availability-of-vista-64-bit-drivers-for-the-nia-neural-impulse-actuator-gaming-peripheral>`_

.. [#foot-background-mindwave] `<http://www.neurosky.com/products/mindwavemobile.aspx>`_

.. [#foot-background-transcend] Android app: `<https://play.google.com/store/apps/details?id=com.personalneuro.transcend>`_

.. [#foot-background-mindset] The experiment used a MindSet headset (the generation before 
   MindWave but with the same chipset and electrode) |nbsp| :cite:p:`crowley_evaluating_2010`.

.. [#foot-background-opi] `<http://op-innovations.com>`_

.. [#foot-background-qt] `<http://qt-project.org>`_

.. [#foot-background-quantified-2013] `<http://quantifiedself.com/conference/Amsterdam-2013>`_

.. [#foot-background-muse] `<http://www.interaxon.ca>`_

.. [#foot-background-insight] `<http://www.kickstarter.com/projects/tanttle/emotiv-insight-optimize-your-brain-fitness-and-per>`_

.. [#foot-background-indiegogo] `<http://www.indiegogo.com/projects/muse-the-brain-sensing-headband-that-lets-you-control-things-with-your-mind>`_

.. [#foot-background-kickstarter] `<http://www.kickstarter.com>`_

.. [#foot-aap] a subset of biofeedback which is the term mentioned in the The American 
   Academy of Pediatrics (AAC) recommendations.

.. [#foot-background-mindball] `<http://www.mindball.se>`_

.. [#foot-background-biozen-app] Android App: `<https://play.google.com/store/apps/details?id=com.t2>`_

.. [#foot-background-biozen] `<http://t2health.org/apps/biozen>`_

.. [#foot-background-smartphonebrainscanner] : `<https://github.com/SmartphoneBrainScanner>`_

