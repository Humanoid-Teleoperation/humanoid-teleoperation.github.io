---
layout: distill
permalink:  /6-design-evaluation/
title: VI. DESIGN & EVALUATION OF HUMANOID TELEOPERATION SYSTEM
nav: false
nav_order: 1
description:
date:
bibliography: humanoid-teleoperation.bib

toc:
  - name: 'A. Evaluation Metrics'
    subsections:
      - name: '1) Usability Assessment'
      - name: '2) Situational Awareness (SA)'
      - name: '3) Workload'
      - name: '4) Engagement, Immersion, Involvement, and Presence'
  - name: 'B. Interface Design and Human-centered Autonomy'
  - name: 'C. Humanoid Robot Teleoperation Design, Evaluation Challenges & Future Directions'
---

In order to deploy the teleoperation system for \textit{real users}, such systems should meet the users' needs and be evaluated prior to deployment. These needs and considerations should be anticipated in the design and development phase.
A human-centered design, consisting in an iterative process aiming at properly allocating the tasks (functions) between the user and the teleoperation system, is required.
Designers need metrics to evaluate the teleoperation systems, to share the knowledge, and compare their findings. These metrics are highly task-dependant, i.e., various tasks impose different functional requirements that the system should meet <d-cite key="Steinfeld2006Common, Goodrich2007Survey"></d-cite>.
These metrics not only determine inherent problems and limitations of the humanoid robot teleoperation system, but also provide guidelines for the design and development, reducing the cost and the time to design such a system.
The rest of this section adopts some metrics proposed in relevant fields that help design and evaluate humanoid robot teleoperation systems.


## A. Evaluation Metrics

### 1) Usability Assessment

According to ISO 9241 <d-cite key="ISO9241"></d-cite>, \textit{usability} is defined as \textit{``the extent to which a system, product or service can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use''.}
In line with this definition and the teleoperation context, effectiveness is the degree of accuracy and completeness in which the user reaches the teleoperation goal, whereas efficiency is related to the resources being used (e.g., time, cost, human effort, etc.) with respect to the achieved outcome <d-cite key="ISO9241"></d-cite>. 
Effectiveness and efficiency are considered as the objective usability measures, which depend on the teleoperation task.
On the other hand, satisfaction determines the degree in which the users' needs and expectations are met as a result of the use of the teleoperation system <d-cite key="ISO9241"></d-cite>. It is determined according to the user's emotional, physical, and cognitive responses.
The user's perceived usability,
which is a subjective measure,
has a direct relation with the user's satisfaction; the more the perceived usability, the higher the satisfaction <d-cite key="Flavian2006Role"></d-cite>.
Moreover, usability assessment is relevant to the individual user in terms of the frequency of use and familiarity with the system.
Some criteria to measure the effectiveness of a task execution are the task completeness, objective achievement, and task errors <d-cite key="Bevan2016New"></d-cite>.
The efficiency of a task execution is established according to the task time, cost-effectiveness, energy consumption, productive time ratio, and unnecessary actions (just a few to mention) <d-cite key="Bevan2016New"></d-cite>.
For the subjective measure of the usability there are some standard empirical and informal techniques to examine the user's perceived usability including concurrent think aloud, retrospective think aloud, concurrent probing, and retrospective probing.
Among these, the most famous one is the System Usability Scale (SUS) <d-cite key="Brooke1996SUS"></d-cite> retrospective probing technique which assesses two factors including  usability as well as learnability for a variety of tasks. Nevertheless, a subjective measure of the usability is in relation with the user perception; therefore, it is affected by the situational awareness, which will be discussed in the next section.
An attempt to provide a holistic taxonomy of usability evaluation in robot teleoperation scenarios is done in <d-cite key="Adamides2014Usability"></d-cite>.


### 2) Situational Awareness (SA)

SA correlates the user capabilities, training, experiences, preconceptions, and objectives with the ongoing task workload together~<d-cite key="endsley1988situation"></d-cite>.
Endsley identified \textit{situation awareness} with three levels as \textit{``the perception of elements in the environment within a volume of time and space, the comprehension of their meaning, and the projection of their status in the near future"}~<d-cite key="endsley1988situation"></d-cite>.
Accordingly,
SA 
tries to understand the process which leads to decision making, considering a variety of elements.


High SA promotes the probability of a good performance, and the poor performance of the task is normally the result of SA loss. SA is lost when the user's knowledge is incomplete or inaccurate, the user attention is narrowed to some elements, or when the mental model of the user diverges from the reality~<d-cite key="endsley1988situation, Nguyen2019Review"></d-cite>.
Loss of SA is also correlated to the workload; when the workload is high the user's attention is drawn from the main task and therefore the user does not give importance to the rest of the elements.

The main works in the literature measuring SA are based on the probe technique, physiological measurements, implicit inference, process indices, and observer ratings~<d-cite key="endsley1988situation, Nguyen2019Review"></d-cite>. Subjective ratings of the SA, where the users fill a form,
are limiting because of the inaccurate evaluation of the users about their SA and the biased evaluation depending on the task outcome~<d-cite key="endsley1988situation"></d-cite>.
To assess SA, EEG and eye-tracking physiological signals are employed as well in the literature. 
SA can be inferred indirectly and implicitly through other related measurable metrics, like the task performance~<d-cite key="Nguyen2019Review"></d-cite>.
Finally, probe techniques can be both retrospective, after task execution, or concurrent, by collecting data with a questionnaire while executing the task.
Among the concurrent ones, the Situation Awareness Global Assessment Technique (SAGAT) proposed by Endsley in~<d-cite key="endsley1988situation"></d-cite> is a freeze-probe approach that measures SA objectively.
This method interrupts the experiment at some random points and halts the user interface,
then a number of questions are asked from the users to evaluate their knowledge about the current and future situation including the user's perception, comprehension, and actions. Later, the responses are compared with the real values collected from the scenario or from experts' responses.
While SAGAT is very reliable, it is intrusive to the natural flow of the task execution.

### 3) Workload

Workload relates the resources demanded by a task to the available resources supplied by the human operator.
There is no consensus about the definition of the workload <d-cite key="Miller2001Workload"></d-cite>;
however, <d-cite key="Hart1988Development"></d-cite> identifies the \textit{workload} as \textit{``the amount of work that is loaded on an individual, the time pressure in which a task is performed, the level of effort exerted, the success in meeting the task requirements, physiological and psychological"}. 
Workload is related to the human operator's (subjective) experience in response to the task objectives.
Especially in time critical decision making tasks, a high workload can lead to user errors or to a delay in the decision making.

Workload presents high variability depending on the human operator and the teleoperation task, hence being difficult to measure.
In fact, the workload is multi-dimensional,
and various subject- and task-related factors (such as mental, physical, information, perceptual, and communication loads) should be considered~<d-cite key=" Miller2001Workload, Hart1988Development"></d-cite>.
Different approaches have been proposed in the literature for measuring the workload on the human operator, namely questionnaires and experts' reports (subjective), physiological techniques, and performance-based approaches~<d-cite key="Miller2001Workload"></d-cite>.
Specifically, for a reliable mental workload assessment a mixture of them is suggested in~<d-cite key="Miller2001Workload"></d-cite>.
Among the subjective measurement methods, the NASA Task Load Index (NASA-TLX) and the Subjective Workload Assessment Technique (SWAT) are the most famous multi dimensional subjective rating methods used in the literature~<d-cite key="Hart1988Development, Reid1988Subjective"></d-cite>.
Continuous physiological measurements such as cardiac activity, eye activity, respiratory activity, speech measures, and brain activity can provide a reliable assessment of the task physical or mental load as well  <d-cite key="Miller2001Workload"></d-cite>
To measure the physical workload, oxygen consumption estimation can directly provide an index, while heart rate can be used as an indirect method.
Moreover, since the workload and task performance have a causal relationship, the task execution performance can play as another indicator of the workload, when time-shared or difficulty of tasks are exploited. An extensive review of the methods to measure the workload can be found in~<d-cite key="Miller2001Workload"></d-cite>.

### 4) Engagement, Immersion, Involvement, and Presence
Some metrics concerning robot teleoperation, specifically related to the subjective experience of the user are engagement, immersion, flow, involvement, and presence.
In different fields, engagement is defined and measured distinctly. In the context of teleoperation, the definition and measurement approaches of engagement are especially relevant in gaming and virtual reality applications.
According to~<d-cite key="bouvier2014defining"></d-cite>, engagement is \textit{``the willingness to have emotions, affect, and thoughts directed towards and aroused by the mediated activity in order to achieve a specific objective''.}
It relies on the user’s activity and expectations. The user is engaged when her/his perceptual, intellectual, and interactional expectations are met.
In this context,  \textit{presence} is characterized as \textit{``the subjective experience of being in one place or environment, even when one is physically situated in another''}  <d-cite key="witmer1998measuring"></d-cite>. Presence is a multifaceted concept that is related to \textit{involvement}, a psychological state  depending on attention to remote environment stimuli, and \textit{immersion}, a psychological state of perceiving oneself as a part of the remote environment stimulus flow <d-cite key="witmer1998measuring"></d-cite>.
Here, stimulus flow is a dynamic stream of sensory information.
There are several factors contributing toward the sense of presence including control, sensory information, distraction, and realism factors.
More information about \textit{presence} can be found in~<d-cite key="witmer1998measuring"></d-cite>.

Even if presence is a subjective sensation, there are both subjective and objective methods to measure it. Subjective measures are based on self-report questionnaires like the ITC-sense of presence inventory <d-cite key="lessiter2001cross"></d-cite> or the Witmer \& Singer Presence Questionnaire <d-cite key="witmer1998measuring"></d-cite>. For objective measures, both behavioral (e.g., startle response) and physiological measures (e.g., heart-rate changes, skin conductance/temperature) are suggested in the literature <d-cite key="riva20037"></d-cite>.
Similar methods have also been exploited to measure the user engagement <d-cite key="rani2005operator"></d-cite>.



## B. Interface Design and Human-centered Autonomy

The interface design impacts the user's decisions while teleoperating the humanoid robot, being the medium of communication between human and robot. Good design choices leverage the user experience and result in a successful teleoperation system.
The diagnostic information provided by different measurement techniques can eventually enhance the design and the user support.
Following the explanation of different metrics provided before, we can identify four types of measurement methods, namely, questionnaire-based subjective ratings, performance-based objective ratings, physiological measures, and behavioral responses.
The subjective rating evaluation is quick, and can be done either online (while performing the task) or retrospectively.
Nevertheless, studies show that retrospective evaluation, while not being intrusive, may be subject to information loss because of the user's bias and poor subject ability to recall.
Physiological measurements are partly related to the concept of \textit{activation} or \textit{arousal} in the field of psychophysiology, which relates the changes of mental effort and its effect on the physiological activity of the human operator~<d-cite key="Roscoe1992Assessing"></d-cite>.
Finally, all the metrics provided are interrelated; for example,~<d-cite key="Riley2004Situation"></d-cite> has studied the effect of SA and task difficulty level on the human performance and the user's sense of telepresence.


The described metrics can be used to identify the robot behaviors that should be automated.
When designing a teleoperation system, one of the critical parameters that impacts the success of the system and the user experience is the autonomy level.
It affects the SA, the user workload, the system usability and the user's sense of presence~<d-cite key="Deng2019Influence"></d-cite>.
While high degree of automation degrades the SA, low autonomy in complex tasks intensifies the workload.
High level of autonomy promotes the user's performance and diminishes the workload in the normal situations~<d-cite key="Kaber2000Design"></d-cite>, while during system failures, a low level of autonomy increases the SA and enhances the human manual performance.
Therefore an intermediate level of autonomy in which the user is in the control loop, i.e., human-centered autonomy, enhances the SA, reduces the workload, and improves the performance against failures~<d-cite key="Kaber2000Design"></d-cite>.


## C. Humanoid Robot Teleoperation Design, Evaluation Challenges & Future Directions

The design of humanoid robots and teleoperation systems are inherently iterative, where the system goes under different evaluations. However, to improve the design, not many studies in the literature have been published to evaluate such systems systematically.
Table \ref{tab:metrics} provides an overview of the works where different metrics are used to enhance and evaluate the teleoperation system. This table demonstrates that fewer behavioral and physiological measurements are employed to evaluate the developed system. We speculate that this is due to the lack of competencies in those fields in the robotics community.
More recently, ANA Avatar XPRIZE <d-cite key="AnaAvatarXprize"></d-cite> took the lead in the evaluation of humanoid robot teleoperation systems by assessing both task performance and subjective measures in locomotion, manipulation, and social interaction scenarios. 
These evaluations can help the developers to choose proper teleoperation devices and adjust the autonomy level, more specifically retargeting and control approaches for humanoid teleoperation according to the architecture presented in Sec.~\ref{fig:retargeting_controller_architecture}.

<!-- \begin{table}
\setlength\tabcolsep{5pt}
\centering
\arrayrulecolor{black}
 \caption{Examples of evaluation metrics for the design and evaluation of robot teleoperation setups.}
\begin{tabular}{|c!{\color{black}\vrule}c|c|c|c|c|c|c|c|c|} 
\hline
\multirow{2}{*}{{ref}}   & \multicolumn{4}{c|}{evaluation metrics}                  & ~                     & \multicolumn{4}{c|}{measurements}   \\ 
\cline{2-5}\cline{7-10}
                                        & {\rotatebox[]{-90}{\makecell{usability}}} & {\rotatebox[]{-90}{\makecell{situational \\ awareness}}} & {\rotatebox[]{-90}{\makecell{workload}}} & {\rotatebox[]{-90}{\makecell{engagement, ~ \\ presence}}} & {\rotatebox[]{-90}{\makecell{ autonomy attentive~ \\ system}}} & {\rotatebox[]{-90}{\makecell{subjective \\ measures}}} & {\rotatebox[]{-90}{\makecell{objective \& task \\performance}}} & {\rotatebox[]{-90}{\makecell{physiological}}} & {\rotatebox[]{-90}{\makecell{behavioural}}} \\ 
\hline\hline
\rowcolor[rgb]{0.906,0.902,0.902} <d-cite key="Villani2017Natural}     & \checkmark            & ~     & ~        & ~          & ~         & ~         & \checkmark         & ~          & ~         \\
<d-cite key="Jankowski2015Usability}                                   & \checkmark            & ~     & ~        & \checkmark          & ~         & \checkmark         & \checkmark         & ~         & ~          \\
\rowcolor[rgb]{0.906,0.902,0.902} <d-cite key="Radmard2015Interface}   & \checkmark            & ~     & \checkmark        & ~          & ~         & \checkmark         & \checkmark         & ~          & ~         \\
<d-cite key="Barros2011Enhancing}                                      & ~         & \checkmark & ~    & ~          & ~         & \checkmark         & \checkmark         & ~          & ~         \\
\rowcolor[rgb]{0.906,0.902,0.902} <d-cite key="Kaber2000Design}        & ~         & \checkmark     & \checkmark        & ~          &  \checkmark         &  \checkmark         &  \checkmark         & ~         & ~          \\
<d-cite key="Riley2004Situation}                                       & ~         & \checkmark     & ~         & \checkmark          &  ~      & \checkmark         & \checkmark         & ~          &  ~         \\
\rowcolor[rgb]{0.906,0.902,0.902} <d-cite key="Lu2019Workload}         & \checkmark            & ~     & \checkmark        & ~          & ~         & \checkmark         & \checkmark         & \checkmark          & ~         \\
<d-cite key="Singh2018Physiologically}                                 & ~         & ~         &   \checkmark       & ~          & \checkmark         & \checkmark         & ~         & \checkmark          & \checkmark       \\
\rowcolor[rgb]{0.906,0.902,0.902} <d-cite key="rani2005operator}       & ~         & ~         & ~        & \checkmark          & \checkmark         & \checkmark         & ~         & \checkmark          & ~         \\
\hline
\end{tabular}
\arrayrulecolor{black}

     \label{tab:metrics}
\end{table} -->


While developing a humanoid robot teleoperation system, different hardware and software components are interleaved in order to perform a task. In the case of poor performances, it is important to consider the interconnection of different components and try to find the sources of the problems.
Another challenge related to teleoperation system development might be latency, which can be related to perception, communication, control, or actuation.
An experimental demonstration provided by~<d-cite key="Lu2019Workload"></d-cite> showed a detrimental impact of the time delay
to the human operator's increased workload as well as the performance. Moreover, the discrepancy of the time delay among different components, e.g., arms, torso, locomotion, hand, and social cues (such as facial expression), can further degrade the teleoperation performance and the user's experience, highlighting the importance of synchronized and coordinated motion, and social cues for the teleoperated humanoid robot.
Unique to humanoid robot teleoperation, having an anthropomorphic humanoid robot body, and a proper selection of teleoperation interfaces, algorithms, and low latency can lead to strong telepresence, or so-called tele-embodiment~<d-cite key="paulos2001social"></d-cite>.


A final challenge in humanoid teleoperation is to build a system that can be easily mastered by non-expert users. State of the art does not often consider any usability assessment or carry out any user study, strongly relying on the expertise and training of a single human operator. From this perspective, we hope that this section helps the reader in identifying the key points and right evaluation metrics for deploying a teleoperation system that meets the user's needs.

