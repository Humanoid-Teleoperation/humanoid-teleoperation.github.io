---
layout: distill
permalink:  /2-teleop-sys-devices/
title: II. TELEOPERATION SYSTEM & DEVICES
nav: false
nav_order: 1
description:
date:
bibliography: humanoid-teleoperation.bib

toc:
  - name: 'A. Teleoperation Architecture'
  - name: 'B. Human Sensory Measurement Devices'
    subsections:
      - name: '1) Human kinematics and dynamics measurements'
      - name: '2) Human physiological measurements'
  - name: 'C. Feedback Interfaces: Robot to Human'
    subsections:
      - name: '1) Visual feedback'
      - name: '2) Haptic feedback'
      - name: '3) Balance feedback'
      - name: '4) Auditory feedback'
  - name: 'D. Graphical User Interfaces (GUIs)'
  
#     # if a section has subsections, you can add them as follows:
#     # subsections:
#     #   - name: Example Child Subsection 1
#     #   - name: Example Child Subsection 2
#   - name: Citations
#   - name: Footnotes
#   - name: Code Blocks
#   - name: Layouts
#   - name: Other Typography?
---


<!-- \begin{figure}[!t]
 \setlength\belowcaptionskip{-0.7\baselineskip}

\centering
\includegraphics[width=\columnwidth]{Figures/teleoperation-architecture-3.pdf}
\caption{Schematic architecture for teleoperating a humanoid.}
\label{fig:teleoperation_architecture}
\end{figure} -->

In the literature, the terms teleoperation and telexistence have been used indistinctly in different contexts. Telexistence refers to the technology that allows human to virtually exist in a remote location through an avatar, experiencing real-time sensations from the remote site <d-cite key="tachitelexistence"></d-cite>. Both the remote environment and the avatar can be real or virtual, but in this article we only consider a real environment and a surrogate humanoid robot as avatar. Telexistence has also been referred to as telepresence in the literature <d-cite key="tachitelexistence"></d-cite>.
The concept of teleoperation, on the other hand, still refers to a human operator remotely controlling a robot, but the focus is mainly put on performing  tasks that require high dexterity in the remote location.
We use these terms interchangeably throughout this survey.
From another perspective, the teleoperation setup represents an interactive system where the robot imitates the human's actions to reach a common objective <d-cite key="Goodrich2007Survey"></d-cite>.

In a teleoperation setup, the user is the person who teleoperates the humanoid robot and identifies the teleoperation goal, i.e. intended outcome, through interfaces. 
The interfaces are the means of the interaction between the user and the robot.
The nature of the exchanging information, constraints, the task requirements, and the degree of shared autonomy determine different preferences on the interface modalities, according to specific metrics which will be discussed later.
Moreover, the choice of the interfaces should make the user feel comfortable, hence enabling a natural and intuitive teleoperation.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/paper/teleoperation-architecture-3.jpg" title="teleop-arch" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Schematic architecture for teleoperating a humanoid.
</div>


## A. Teleoperation Architecture
Fig. 2 shows a schematic view of the architecture for teleoperating a humanoid robot. 
First, human kinematic and dynamic information are measured and transmitted to the humanoid robot motion for teleoperation.
More complex retargeting methods (i.e., mapping of the human motion to the robot motion), employed in assisted teleoperation systems (Sec.~\ref{sec:AssistedTele}), may need the estimation of the user reaction forces/torques.
There are cases in which also physiological signals are measured in order to estimate the psychophysiological state of the user, which can help enhancing the performance of the teleoperation.
On the basis of the estimated states, the retargeting policy is selected and the references are provided to the robot accordingly.
Teleoperation systems are employed not only for telemanipulation scenarios but also for social teleinteractions (i.e. remotely interacting with other people). In this case, the robot's anthropomorphic motion and social cues such as facial expressions can enhance the interaction experience. Therefore, rich human sensory information is indispensable.



To effectively teleoperate the robot, the user should make proper decisions; therefore he/she should receive various feedback from the remote environment and the robot.
In many cases, the sensors for perceiving the human data and the technology to provide feedback to the user are integrated together in an interface.
In the rest of the section, we will discuss  different available interfaces and sensor technologies in teleoperation scenarios,
whereas their design and evaluation will be discussed later in Sec.~\ref{sec:EvaluationMetrics}.

The retargeting block (Fig. 2) maps human sensory information to the reference behavior for the robot teleoperation, hence the human can be considered as master or leader, and the robot as slave or follower.
We can discern two retargeting strategies: unilateral and bilateral teleoperation. In the unilateral approach, the coupling between the human and robot takes place only in one direction.
The human operator can still receive haptic feedback either as a kinesthetic cue not directly related to the contact force being generated by the robot or as an indirect force in a passive part of her/his body not commanding the robot.
But in bilateral systems, human and humanoid robot are directly coupled. The choice of bilateral retargeting depends on the task, communication rate, and degree of shared autonomy, as will be discussed~in~Sec.~\ref{sec:AssistedTele}.

The human retargeted information, together with the feedback from the robot, are streamed over a communication channel that could be non-ideal. In fact, long distances between the operator and the robot or poor network conditions may induce delays in the flow of information, packet loss and limited bandwidth, adversely affecting the teleoperation experience.
Sec.~\ref{sec:CommunicationChannel} details the approaches in the literature to teleoperate robots in such conditions.
Finally, the robot local control loop
generates
the low level commands- i.e., joints position, velocity, or torque references- to the robot, taking into account the human references (Sec.~\ref{sec:RobotControl}).

<!-- #%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% -->
<!-- %%%%%%%%%%%%%%%%%%%%%%% HUMAN INPUT %%%%%%%%%%%%%%%%%%%%%%%%%%% -->
<!-- %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% -->
## B. Human Sensory Measurement Devices
In this section, we provide a detailed description of the technologies available to sense various human states,
including the advances to measure the human motion, the physiological states, and the interaction forces with the environment.
We report in TABLE 1 the various measurement devices adopted so far for humanoid robot teleoperation.


<!-- %%%%%%%%%%%%%%%%%%%%%%%%% -->
### 1) Human kinematics and dynamics measurements
To provide the references for the robot motion, we need to sense human intentions.
For simple teleoperation cases, the measurements may be granted through simple interfaces such as keyboard, mouse, or joystick commands <d-cite key="ando2020master"></d-cite>.
However, for a more complex system like a humanoid robot, those simple interfaces may not be enough, especially when the user wants to exert a high level of control authority over the robot. Therefore, the need for natural interfaces for effectively commanding the robot arises. 
We can consider solutions benefiting from the similarity of the human and the humanoid robot anthropomorphic geometries, i.e., providing the references to the robot limbs with spatial analogies to those of the human (natural mapping).
Therefore, the need to measure the human kinematics emerges.

Different technologies have been employed in the literature to measure the motion of the main human limbs, such as legs, torso, arms, head, and hands. 
An ubiquitous option are the Inertial Measurement Unit (IMU)-based wearable technologies. In this context,
two cases are possible,
a segregated set of IMU sensors are used throughout the body to measure the human motion 
or an integrated network of sensors is used throughout the human body <d-cite key="darvish2019, penco2019"></d-cite>.
The former case normally provides the raw IMU values, while the latter provides the information of the human limb movements.
In the second case,
a calibration process computes the sensors transformations with respect to body segments <d-cite key="roetenberg2009xsens"></d-cite>. This technology is especially of interest because of the high accuracy and frequency of the retrieved human motion information
without the occlusion problem.
However, its accuracy may suffer from disturbances caused by the magnetic field and displacement of the sensors with respect to their initial emplacement.
Yet, another recent wearable technology to capture the hand pose is a stretchable soft glove embedded with distributed capacitive sensors <d-cite key="glauser2019interactive"></d-cite>.
A review about the textile-based wearable technology used to estimate the human kinematics is provided in <d-cite key="wang2020textile"></d-cite>.

Optical sensors are another technology used to capture the human motion, with active and passive variants. In the active case, the reflection of the pattern is sensed by the optical sensors. Some of the employed technologies include depth sensors and optical motion capture systems.
In the case of passive sensors, RGB monocular cameras (regular cameras) or binocular cameras (stereo cameras) are used to track the human motions. Thanks to the optical sensors, a skeleton of the human body is generated and tracked in 2-D or 3-D Cartesian space. The main problems with these methods are the occlusion and the low portability of the setup.

To track the users' motion in bilateral teleoperation scenarios, exoskeletons are often used.
In this case, the exoskeleton model and the encoder data are fed to the forward kinematics to estimate the human link's poses and velocities~<d-cite key="ramos2019dynamic, ishiguro2020bilateral"></d-cite>.


The previously introduced technologies can be used to measure the human gait information with locomotion analysis.
Conventional or omnidirectional treadmills are employed in the literature for this purpose~<d-cite key=" elobaid2018a"></d-cite>. While the treadmill can be used for even terrains, it would not work to retarget locomotion on uneven terrains.
To respond to this shortcoming, a cockpit-like teleoperation setup has been recently proposed~<d-cite key="ishiguro2020bilateral"></d-cite>.
To estimate the interaction forces between the human and the teleoperation setup, force-torque sensors measuring the human wrenches can be integrated in ground plates, shoes, or exoskeletons.
Richer information can be obtained by distributed capacitance sensors that measure the pressure manifold. 

<!-- %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% -->
<!-- %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% -->

<!-- 

\begin{table*}
  \setlength\belowcaptionskip{-0.7\baselineskip}

\setlength\tabcolsep{1.5pt} % default value: 6pt
\centering
\arrayrulecolor{black}
\caption{Main works and technologies related to the teleoperation of humanoids.}
\begin{tabular}{|c|c|c|c|c|c|c|c|c|c|c|c|c|c|c|c|c|c|c|c|c|c|c|c|c|c|} 
\hline
\multirow{4}{*}{ ref} &
\multirow{4}{*}{ robot} &
\multicolumn{11}{c|}{teleoperation devices} &
\multicolumn{4}{c|}{retargeting \& planning} &
\multicolumn{3}{c|}{stabilizer} &
% \multicolumn{4}{c|}{whole-body \\ controller} &
\multicolumn{4}{c|}{ \makecell{whole-body \\ controller}} &
% \multicolumn{2}{c|}{low−level joint \\ controller}
\multicolumn{2}{c|}{ \makecell{low-level \\ joint control}} \\
\cline{3-26}
                     &
                     &
                     \multicolumn{4}{c!{\color{black}\vrule}}{ \makecell{ human motion \\ measurement} }    &
                     \multicolumn{7}{c!{\color{black}\vrule}}{feedback} & 
                     \multirow{3}{*}{\rotatebox[]{-90}{\makecell{~GUI-based planner}}} & 
                     \multicolumn{3}{c!{\color{black}\vrule}}{\makecell{retargeting \& motion \\ generation}} & 
                     \multirow{3}{*}{\rotatebox[]{-90}{\makecell{~ZMP}}} &
                     \multirow{3}{*}{\rotatebox[]{-90}{\makecell{~DCM-ZMP}}} & 
                     \multirow{3}{*}{\rotatebox[]{-90}{\makecell{~contact wrench, \\  force distribution }}} &
                     \multirow{3}{*}{\rotatebox[]{-90}{\makecell{~IK/velocity IK}}} &
                     \multirow{3}{*}{\rotatebox[]{-90}{\makecell{~inverse dynamics}}} & 
                     \multirow{3}{*}{\rotatebox[]{-90}{\makecell{~momentum-based}}} & 
                     \multirow{3}{*}{\rotatebox[]{-90}{\makecell{~QP method}}} & 
                     \multirow{3}{0.6cm}{\rotatebox[]{-90}{\makecell{~joint position}}} & 
                     \multirow{3}{0.6cm}{\rotatebox[]{-90}{\makecell{~joint torque}}} \\ 
\cline{3-13}\cline{15-17}
                     &
                     &
                     \multirow{2}{*}{\rotatebox[]{-90}{\makecell{~motion-capture \\ suit}}} &
                     \multirow{2}{*}{\rotatebox[]{-90}{\makecell{ ~optical-tracking}}} &
                     \multirow{2}{*}{\rotatebox[]{-90}{\makecell{ ~~~~~exoskeleton}}} &
                     \multirow{2}{*}{\rotatebox[]{-90}{\makecell{ mouse,keyboard,\\ \,joystick,treadmill~}}} &
                     \multicolumn{2}{c!{\color{black}\vrule}}{visual} &
                     \multicolumn{5}{c!{\color{black}\vrule}}{haptic}    &
                     &
                     %\multirow{2}{*}{\rotatebox[]{-90}{\makecell{~search-based}}} &
                     %\multirow{2}{*}{\rotatebox[]{-90}{\makecell{~dynamical system \\ optimization}}} &
                     \multirow{2}{*}{\rotatebox[]{-90}{\makecell{~footstep  motion \\ generation}}} &
                     \multirow{2}{*}{\rotatebox[]{-90}{\makecell{~upper-body \\ retargeting}}} &
                     \multirow{2}{*}{\rotatebox[]{-90}{\makecell{~whole-body \\ retargeting}}} &
                      &
                      &
                      &
                      &
                      &
                      &
                      &
                      &
                      \\
\cline{7-13}

                     &
                     &
                     & 
                     &   
                     &       
                     & 
                     \rotatebox[]{-90}{\makecell{ ~mono display, \\GUI~}} &
                     \rotatebox[]{-90}{\makecell{ ~Stereo, \\ AR/VR headset~}} &
                     \rotatebox[]{-90}{\makecell{ ~whole-body \\ exoskeleton}} & 
                     \rotatebox[]{-90}{\makecell{ ~dual-arm \\exoskeleton}} &
                     \rotatebox[]{-90}{\makecell{ ~glove}} & 
                     \rotatebox[]{-90}{\makecell{ ~balance}} & 
                     \rotatebox[]{-90}{\makecell{ ~vibrotactile}} & 
                     &           
                     &              
                     &                 
                     &                 
                     &              
                     &              
                     &                 
                     &          
                     &   
                     &
                     &            
                     &            
                     \\  
\hline\hline


\rowcolor{Gray}
\cite{tachi2020telesar} & TELESAR VI & ~  & \checkmark & ~ & ~ & ~ & \checkmark & ~ & ~ & \checkmark & ~ & ~         & ~       & ~ & ~ & \checkmark          & ~ & ~ & ~      & \checkmark & ~ & ~ & ~ & \checkmark & ~  \\ 

\cite{hu2014}  & TORO & \checkmark & ~ & ~ & ~ & ~ & ~ & ~ & ~ & ~ & ~ & ~ 
  & ~         & ~ & ~ & \checkmark         & ~ & \checkmark & ~         & \checkmark & ~ & ~ & \checkmark         & \checkmark & ~ \\ 

\rowcolor{Gray}
\cite{abi2018}  & TORO & ~ & ~ & \checkmark & ~ & ~ & ~ & ~ & \checkmark & ~ & ~ & ~
& ~         & ~ & ~ & ~         & ~ & ~ & \checkmark         &  ~ & ~ & \checkmark & \checkmark         & ~ & \checkmark \\

\cite{ishiguro2018} & JAXON & ~ & \checkmark & ~ & ~ & ~ & \checkmark & ~ & ~ & ~ & ~ & ~
& ~          & ~ & ~ & \checkmark         & ~ & \checkmark & ~         & \checkmark & ~ & ~ & ~         & \checkmark & ~ \\ 

\rowcolor{Gray}
\cite{ishiguro2020bilateral}  & JAXON & ~ & ~ & \checkmark & ~ & ~ & \checkmark & \checkmark & ~ & ~ & ~ & ~
& ~        & ~ & ~ & \checkmark         & ~ & \checkmark & ~         & \checkmark & ~ & ~ & ~         & \checkmark & ~ \\ 

\cite{jorgensen2019}  & Valkyrie & ~ & ~ & ~ & \checkmark & \checkmark & ~ & ~ & ~ & ~ & ~ & ~ 
& \checkmark          & \checkmark & ~ & ~         & ~ & ~ & \checkmark         & ~ & \checkmark & \checkmark & \checkmark         & ~ & \checkmark \\ 


\rowcolor{Gray}
\cite{johnson2017team}  & Atlas & ~ & ~ & ~ & \checkmark & \checkmark & ~ & ~ & ~ & ~ & ~ & ~
& ~          & \checkmark & ~ & ~         & ~ & ~ & \checkmark         & ~ & \checkmark & \checkmark & \checkmark         & ~ & \checkmark \\ 


\cite{zucker2015} & DRC-Hubo Beta & ~ & ~ & ~ & \checkmark & \checkmark & ~ & ~ & ~ & ~ & ~ & ~ 
& \checkmark          & \checkmark & ~ & ~         & \checkmark & ~ & ~         & \checkmark & ~ & ~ & ~         & ~ & \checkmark \\ 

\rowcolor{Gray}
\cite{chagas2021humanoid}  &  DRC-Hubo &           ~  & \checkmark & ~ & \checkmark         & ~ & \checkmark         & ~  & ~ & ~ & ~ & ~                  & ~          & \checkmark & \checkmark & ~         & \checkmark & ~ & ~         & \checkmark & ~ & ~ & ~         & \checkmark & ~ \\ 

\cite{eramos2015}  & HRP-2  & ~ & \checkmark & ~ & ~ & ~ & ~ & ~ & ~ & ~ & ~ & ~
& ~           & \checkmark &  ~ & \checkmark         & \checkmark & ~ & ~         & ~ & \checkmark & ~ & \checkmark         & ~ & ~ \\ 

\rowcolor{Gray}
\cite{cisneros2016}  & HRP-2KAI & ~ & ~ & ~ & \checkmark & \checkmark & ~ & ~ & ~ & ~ & ~ & ~ 
& \checkmark           & ~ & ~ & ~         & ~ & \checkmark & \checkmark         & \checkmark & ~ & ~ & ~         & \checkmark & ~ \\ 



\cite{difava2016}  & HRP-4 & \checkmark & ~ & ~ & ~ & ~ & ~ & ~ & ~ & ~ & ~ & ~
& ~           & ~ & ~ & \checkmark         & ~ & ~ & ~         & ~ & \checkmark & ~ & \checkmark         & \checkmark & ~ \\ 

\rowcolor{Gray}
\cite{Cisneros2022Team}  &  HRP-4CR &           \checkmark  & ~ & ~ & \checkmark         & ~ & \checkmark         & ~  & ~ & ~ & ~ & \checkmark                  & ~          & \checkmark & \checkmark & ~         & ~ & \checkmark & ~         & ~ & ~ & ~ & \checkmark         & \checkmark & ~ \\ 



\cite{ramos2018}  & little HERMES & ~ & ~ & \checkmark & ~  & ~ & \checkmark & \checkmark & ~ & ~ & \checkmark & ~ 
& ~           & ~ & ~ & ~         & ~ & ~ & \checkmark         & ~ & ~ & \checkmark & ~         & ~ & \checkmark \\ 


\rowcolor{Gray}
\cite{peternel2013}  & Fujitsu HOAP-3 & ~ & \checkmark & ~ & ~ & ~ & ~ & ~ & ~ & ~ & \checkmark & ~
& ~           & ~ & ~ & ~         & ~ & ~ & ~         & ~ & ~ & ~ & ~         & \checkmark & ~ \\ 


\cite{brygo2014b}  & COMAN & ~ & \checkmark & ~ & ~ & ~ & ~ & ~ & ~ & ~ & \checkmark & \checkmark 
& ~          & ~ & ~ & ~         & ~ & ~ & ~         & \checkmark & ~ & ~ & ~         & \checkmark & ~ \\ 


\rowcolor{Gray}
\cite{kim2013}  & MAHRU & \checkmark & ~ & ~ & ~ & ~ & \checkmark & ~ & ~ & ~ & ~ & ~ 
& ~           & \checkmark & \checkmark & ~         & ~ & \checkmark & ~         & \checkmark & ~ & ~ & ~         & \checkmark & ~ \\ 


\cite{penco2019}  & iCub & \checkmark & ~ & ~ & \checkmark & ~ & \checkmark & ~ & ~ & ~ & ~ & ~
& ~          & ~ & ~ & \checkmark         & \checkmark & ~ & ~         & \checkmark & ~ & ~ & \checkmark         & \checkmark & ~ \\ 


\rowcolor{Gray}
\cite{elobaid2018a}  &iCub & ~ & \checkmark & ~ & \checkmark & ~ & \checkmark & ~ & ~ & ~ & ~ & ~ 
& ~           & \checkmark & \checkmark & ~         & ~ & \checkmark & ~         & \checkmark & ~ & ~ & \checkmark         & \checkmark & ~ \\ 


\cite{darvish2019}  &  iCub & \checkmark  & ~ & ~ & \checkmark  & ~ & \checkmark & ~  & ~ & ~ & ~ & ~ 
& ~           & \checkmark & \checkmark & \checkmark         & ~ & \checkmark & ~         & \checkmark & ~ & \checkmark & \checkmark         & \checkmark & \checkmark \\ 


\rowcolor{Gray}
\cite{dafarra2022icub3}  &  iCub3 &           \checkmark  & \checkmark & ~ & \checkmark         & ~ & \checkmark         & ~  & ~ & \checkmark & ~ & \checkmark                  & ~           & \checkmark & \checkmark & ~         & ~ & \checkmark & ~         & \checkmark & ~ & ~ & \checkmark         & \checkmark & ~ \\ 


\cite{schwarz2021nimbro}  &  NimbRo Avatar &           ~  & ~ & \checkmark & \checkmark         & ~ & \checkmark         & ~  & \checkmark & \checkmark & ~ & ~                  & ~          & ~ & \checkmark & ~         & ~ & ~ & ~         & ~ & ~ & ~ & ~         & ~ & \checkmark \\ 




% \cite{}  &  Name &           ~  & ~ & ~ & ~         & ~ & ~         & ~  & ~ & ~ & ~ & ~                  & ~ & ~         & ~ & ~ & ~         & ~ & ~ & ~         & ~ & ~ & ~ & ~         & ~ & ~ \\ 

\hline
\end{tabular}
\arrayrulecolor{black}

\label{tab:teleoperation}
\end{table*} -->


<!-- %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% -->
### 2) Human physiological measurements
Among the different sensors available to measure human physiological activities, we briefly describe those that have been mostly used in teleoperation and robotics literature. 
An electromyography (EMG) sensor provides a measure of the muscle activity, i.e., contraction, in response to the neural stimulation action potential <d-cite key="staudenmann2010methodological"></d-cite>. It works by measuring the difference between the electrical potential generated in the muscle fibres by employing two or more electrodes. There are two types of EMG sensors, the surface EMG and the intramuscular EMG. The former records the muscle activity from above the skin (therefore, noninvasive), while the latter measures the muscle activity by inserting needle electrodes into the muscle (intrusive). The main problem with EMG sensors, especially the surface one, is the low signal to noise ratio, which is the main barrier for a desirable performance <d-cite key="chowdhury2013surface"></d-cite>. The EMG signals are used in the literature for teleoperating a robot or a prosthesis,  
for estimation of the human effort and muscle forces <d-cite key="staudenmann2010methodological"></d-cite>, or for estimation of the muscle stiffness. The EMG signals can anticipate human motions by measuring the muscle activities within a few milliseconds in advance of force generation; this could be exploited to anticipate the human operator's motion, enhancing the teleoperation. 

Electroencephalography (EEG) sensors can be employed to identify the user mental state. They are most widely used in non-invasive brain-machine interface (BMI) and they monitor the brainwaves resulting from the neural activity of the brain.
The measurement is done by placing several electrodes on the scalp and measuring the small electrical signal fluctuations <d-cite key="niedermeyer2005electroencephalography"></d-cite>.
Other sensors that could be employed in a telexistence scenario for an advanced estimation of the human psycho-physiological state include the Heart Rate Monitor sensors, which estimate the maximal uptake of the oxygen and the heart rate variability <d-cite key="achten2003heart"></d-cite>, useful to measure the user's fatigue, Electro-Oculography (EOG) sensors or video-based eye-trackers, which estimate of gaze position based on the pupil or iris position <d-cite key="sugano2015self"></d-cite>, important for the visual feedback given by Virtual Reality (VR) or Augmented Reality (AR) goggles; and capacitive thin-film humidity sensors, which measure the humidity of the gas-flow of the human skin <d-cite key="ohhashi1998human"></d-cite>, a good indicator of the human emotional stimuli and stress level. 

<!-- %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%% FEEDBACK %%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% -->
## C. Feedback Interfaces: Robot to Human
\label{sec:FeedbackInterfaceDevices}
A crucial point in robot teleoperation is to sufficiently inform the human operator of the states of the robot and its work site, so that she/he can comprehend the situation or feel physically present at the site, producing effective robot behaviors.
TABLE 1 summarizes the different feedback devices that have been adopted for humanoid teleoperation.

<!-- %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% -->
### 1) Visual feedback
A conventional way to provide situation awareness to the human operator is through visual feedback. Visual information allows the user to localize themselves and other humans or objects in the remote environment.
Graphical User Interfaces (GUIs) were widely used by the teams participating at the DRC to remotely pilot their robots through the competition tasks~<d-cite key="johnson2017team,cisneros2016,zucker2015"></d-cite>. 
Not only the information coming from the RGB cameras of the robot but also other information such as depth, LIDAR, RADAR, and thermographic maps of the remote environment was displayed to the user.

An alternative way to give visual feedback to the human operator is through VR headsets, connected to the robot cameras.
Although this has been demonstrated to be effective in several robotic experiments <d-cite key="kim2013,ishiguro2018,darvish2019,penco2019"></d-cite>, during locomotion the users often suffer from
motion sickness, since the images from the robot cameras are not stabilized, while the images perceived by the human eyes are automatically stabilized on the retina thanks to compensatory eye reflexes.
This aspect could be improved by adopting digital image stabilization techniques or AR  <d-cite key="2010ryueyes"></d-cite>.
Another issue concerning the visual feedback is related to the limited bandwidth of the communication link, which can delay the stream of information.
Also, human reaction time to visual input is inherently slow ($\approx$250-300 ms), so a higher delay in the stream of information can be perceived by the user and further aggravate the motion sickness. If also haptic feedback is streamed to the operator, then even lower delays can be disturbing. In fact, human reaction to haptic information is much faster (around 100-150ms).


<!-- %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% -->
### 2) Haptic feedback
Visual feedback is not often sufficient for many real-world applications, especially those involving power manipulation (with high forces) or interaction with other human subjects, where the dynamics of the robot, the contact forces with the environment, and the human-robot interaction forces are of crucial importance. In such scenarios also the haptic feedback is required to exploit the human operator's motor skills in order to augment the robot performance. 

There are different technologies available in the literature to provide haptic feedback to the human. Force feedback, tactile and vibro-tactile feedback are the most used in teleoperation scenarios.
The interface providing kinesthetic force feedback can be similar to an exoskeleton <d-cite key="Wang2015"></d-cite> or can be cable driven.
The latter only provides a tension force feedback, while the former provides the force feedback on different directions. 
Dual-arm exoskeletons have been proposed to guide the teleoperated robot during manipulation tasks while receiving haptic feedback through the same actuated exoskeleton arms <d-cite key="tachitelexistence, abi2018"></d-cite> and recently also a whole-body exoskeleton cockpit has been proposed to teleoperate the JAXON humanoid robot during heavy manipulation tasks and stepping on uneven terrains <d-cite key="ishiguro2020bilateral"></d-cite>, getting a force feedback on the whole limbs.

To convey the sense of touch, tactile displays have been adopted in the literature <d-cite key="wagner2004design"></d-cite>.
These can also provide temperature feedback to the user.
Other employed haptic feedbacks are vibrotactile and air pressure ones, used as a sensory substitution to transmit senses of touch, texture, forces, suggesting directions, or to catch the attention of the user <d-cite key="brygo2014b"></d-cite>.

All these types of haptic feedback are combined in the telexistence system TELESAR V <d-cite key="tachitelexistence"></d-cite>, which has been developed to provide complete cutaneous sensations to the human operator.
The idea is that different physical stimuli give rise to the same sensation in humans and are perceived as identical. This is due to the the fact that human skin has limited receptors and can perceive only force, vibration, and temperature, which in <d-cite key="hapticcolors"></d-cite> are defined as \textit{haptic primary colors}. It is thus sufficient to combine these \textit{colors} in order to reproduce any cutaneous sensation without actually touching the real object.

<!-- %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% -->
### 3) Balance feedback
Haptic feedback can also be used to transmit to the operator a sense of the robot's balance.
The idea behind the balance feedback is to transfer to the operator the information about the \textit{effect of disturbances} over the robot dynamics or stability instead of directly mapping to the human the disturbance forces applied to the robot. 
In <d-cite key="brygo2014b"></d-cite>, Brygo \textit{et al.} proposed to provide the feedback of the robot’s balance state by means of a vibro-tactile belt.
Also, Peternel and Babic~<d-cite key="peternel2013"></d-cite> proposed a cable-driven haptic interface that maps the state of the robot’s balance to the human demonstrator.
Alternatively, Abi-Farrajil \textit{et al.}~<d-cite key="abi2018"></d-cite> introduced a task-relevant haptic feedback interface composed by two light-weight robotic arms that receives high-level informative haptic cues informing the user about the impact of her/his potential actions on the robot’s balance. 
These studies do not investigate the case of dynamic behaviors, but are rather limited to double support scenarios.
In~<d-cite key="ramos2018"></d-cite> instead, simultaneous stepping is enabled via bilateral coupling between the human operator, wearing a Balance Feedback Interface (BFI), and the robot. The BFI is composed of an passive exoskeleton which captures human body posture and a parallel mechanism which applies feedback forces to the operator's torso.
<!-- %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% -->
### 4) Auditory feedback
Auditory feedback is another means of communication. It is mainly provided to the user through headphones, single or multiple speakers. Auditory information can be used for different purposes: to enable the user to communicate with others in the remote environment through the robot, to increase the user situational awareness, to localize the sound source by using several microphones, or to detect the collision of the robot links with the environment. 
The user and the teleoperated robot may also communicate through the audio channel; e.g., for state transitions.

## D. Graphical User Interfaces (GUIs)
GUIs are used in the literature to provide both feedback to the user and give commands to the robot.
In the DRC, operators were able to supervise the task execution through a task panel, using manual interfaces in case they needed to make corrections. 
The main window consisted of a 2D and 3D visualization environment, the robot’s current and goal states, motion plans, together with other perception sensor data such as hardware driver status~<d-cite key="nakaoka2015task, zucker2015"></d-cite>.
Due to the limited robot cognitive skills, perception tasks were shared among the users and the robot. 

A common approach adopted by the different teams was to guide the robot perception algorithms to fit the object models to the point cloud, used to estimate the 3D pose of objects of interest in the environment. For example, operators were annotating search regions by clicking on displayed camera images or by clicking on 3D positions in the point cloud.
Following that, markers were used to identify the goal pose of the robot arm end effectors <d-cite key="johnson2017team"></d-cite>, the robot configuration, or with a higher autonomy level to define the goal pose of objects for manipulation tasks <d-cite key="nakaoka2015task"></d-cite>.
In these cases, robots tried to find an obstacle-free path (related to Sec. \ref{sec:kinematic-retargeting::high-level}), and show the generated path to the operator for verification prior to execution~<d-cite key="nakaoka2015task"></d-cite>.
Throughout this process, the robots' lower-body teleoperation was treated differently. When the robot's desired base/CoM goal or footsteps were marked by the user, an obstacle-free path (Sec.~\ref{sec:kinematic-retargeting::high-level}) and footsteps trajectories were automatically generated (Sec.~\ref{sec:kinematic-retargeting::low-level}). In this process, footsteps were adjusted to uneven terrain given the estimated height-field data~<d-cite key="nakaoka2015task"></d-cite>.

GUIs have also been used to command frequent high-level tasks to the robot by encoding them as state machines or as task sequences~<d-cite key="nakaoka2015task"></d-cite>.
In DRC open-source software tools, such as RViz and Choreonoid, were commonly used~<d-cite key="zucker2015, nakaoka2015task"></d-cite>.
Custom functionalities were added to them using software plugins. Today, many of these functionalities can be integrated with VR and AR
devices.
