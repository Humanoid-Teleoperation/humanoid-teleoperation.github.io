---
layout: distill
permalink:  /5-communication/
title: V. COMMUNICATION CHANNEL
nav: false
nav_order: 1
description:
date:
bibliography: humanoid-teleoperation.bib

toc:
  - name: 'A. Transmission delays'
  - name: 'B. Distortion'
  - name: 'C. Network-based Model'
  - name: 'D. Passivity'
  - name: 'E. Stability of Time-delayed Humanoid Robot Teleoperation'
  
---

In teleoperation, human and humanoid robot transmit information through a _communication channel_ <d-cite key="Bemporad_CDC1998"></d-cite>.
However, the communication channel introduces complexities that impact the stability and performance of the teleoperation, namely, transmission delays, and distortion of the information.
		
## A. Transmission delays

The interest for the transmission delays in teleoperation emerged back in the 60s.
The first research to consider the effect of these transmission delays on the performance of the teleoperation was published by Ferrel <d-cite key="Ferrel_THFE1965"></d-cite>. 
He realized that when a delay is inserted most operators adopt an effective _move-and-wait_ strategy.
However, as he did not consider force reflection there was no problem of instability.
Only when force reflection was considered, instability became apparent.
			
As a consequence, most of the early research on teleoperation targeting delays was based on
supervisory and software-based teleoperation, without	_closing the loop_ in force.
Some examples are the employment of high-level commands and stored subroutines,
or a predictive display that gives the operator a
prediction of the system response <d-cite key="Bemporad_CDC1998"></d-cite>.
			
Although old, these techniques are still in use when dealing with extremely complex robots,
as humanoid robots are.
As an example, the robots that participated during the DRC
had to deal	with a communication channel represented by two links:
\begin{inparaenum}[(a)]
\item a bi-directional low bandwidth (9600 bps) continuous communication path, or
\item a unidirectional high bandwidth (300 Mbps) communication path with intermittent connection.
\end{inparaenum}
The purpose was to boost the autonomy of the robots.
As a result, most of the teams employed high-level commands, visual aids, and no bilateral
teleoperation <d-cite key="feng2015optimization"></d-cite>.
The effect of the _``move-and-wait''_ strategy was apparent, and greatly influenced the operation speed.
			
A real sense of telepresence can only be achieved by	kinesthetically coupling the operator to the remote environment by
introducing force reflection <d-cite key="hokayem2006bilateral"></d-cite>.
However, time delay can represent a destabilizing factor unless the motion bandwidth is severely reduced
or more advanced solutions are considered.
Shared-control solutions can also be adopted to handle communication
delays <d-cite key="liu2013"></d-cite>.
Even round-trip delays around 100 ms (typical of the Internet) in fact, can induce the instability of the teleoperation system either indirectly, due to human operator's overcompensations of the delayed perceived errors <d-cite key="ferrell1965"></d-cite>, or directly in the control law in the case of bilateral systems.

Advanced techniques to deal with delays appeared in the mid 80s.
Particularly, using _network theory_ and the concept of passivity allowed to achieve stable
time-delayed teleoperation assuming constant-time delays <d-cite key="Anderson_IJRR1992"></d-cite> <d-cite key="Niemeyer_JOE1991"></d-cite>.
The _constant-time delay_ assumption is limited and valid for simple communication channels.
Packet switched networks, as it is the case of Internet, introduce additional difficulties:
\begin{inparaenum}[(a)]
\item random varying delays that can reach very high values,
\item a discrete-time exchange of information,
\item the effect of quantization, and
\item loss of packets <d-cite key="hokayem2006bilateral"></d-cite>.
\end{inparaenum}
Varying-time delays appear due to several factors like traffic congestion, bandwidth, and information loss.
The latter mainly caused by transmission time-outs, transmission errors, and a limited buffer size.
To deal with the varying-time delay,
one can
estimate an upper bound of the delay
through networks statistics, then use it to dissipate energy <d-cite key="Lozano_Mechatronics2002"></d-cite>,
to emulate a virtual constant-time delay <d-cite key="Kosuge_ICRA1996"></d-cite>, or to use it to extend the horizon of a model predictive control <d-cite key="Bemporad_CDC1998"></d-cite>.

## B. Distortion
			
Distortion is another effect introduced by the communication channel.
In case of packet switched networks, a delay of discrete-time velocity information results in a distortion of velocity and position drift, hence, degrading the performance.
Solutions to this problem can include the exchange of position information together with the velocity, or time-stamping the information <d-cite key="Chopra_ACC2003"></d-cite>.
Another source of distortion is due to the policies introduced when there is information loss:
\begin{inparaenum}[(a)]
\item to treat the lost packet as a null packet,
\item to use the last valid packet, or
\item to use interpolation <d-cite key="hokayem2006bilateral"></d-cite>.
\end{inparaenum}
			
## C. Network-based Model

The standard model of the communication channel is based on network theory.
By using an analogy between mechanical and electrical systems, we can represent the teleoperation system as
a network of interconnected $n$-ports. 
An $n$-port is characterized by the relationship between _effort_ $f$ (voltage or force) and _flow_ $v$ (current or velocity).

Assuming that we have flows and efforts on both sides of a 2-port network representing a Linear Time-Invariant
(LTI) system, the relationship between them can be written (in the frequency domain) by a hybrid matrix.
The idea is to use control to modify the characteristics of this matrix in order to overcome the difficulties imposed by the communication channel <d-cite key="hokayem2006bilateral"></d-cite>.
In the topic of bilateral teleoperation represented by a nonlinear system, which is the case for humanoid robots, the frequency-domain approach is no longer valid.
However, Anderson <d-cite key="Anderson_IJRR1992"></d-cite> demonstrated that by using a Hilbert network, with efforts and flows
belonging to a Hilbert space, equivalent analyses could be performed.
			
## D. Passivity

The passivity formalism provides a simple and robust tool to analyze the stability of a nonlinear system <d-cite key="Niemeyer_JOE1991"></d-cite>.
A passive system may dissipate energy ($E(t)$) but it cannot increase its total energy <d-cite key="Anderson_TAC1989"></d-cite>.
For an $n$-port, we can take forces as inputs and velocities as outputs, and define the _power_
(not necessarily a physical one) entering to the system as the scalar product between input and output
($P(t) = f^T(t) v(t)$).
Then, for an $n$-port to be passive, the power is either stored or dissipated:
\begin{equation}
\int_0^t f^T(\tau) v(\tau) d\tau = E(t) - E(0) + \int_0^t P_\text{diss} d\tau
\geq -E(0),
\end{equation}
where $P_\text{diss}$ is a non-negative power dissipation function. If no power is dissipated, the $n$-port is lossless <d-cite key="Niemeyer_JOE1991"></d-cite>.



An important tool that can be used to analyze the passivity
is _scattering theory_, which relates the effort and flow of a network through a _scattering operator_ <d-cite key="Anderson_TAC1989, hokayem2006bilateral"></d-cite>.
In this respect, a passivity-based system imitates a physical system that obeys energy conservation
<d-cite key="Niemeyer_JOE1991"></d-cite>.
An important property of passive systems is that the stored energy and power dissipation of a combined system is equal to the sum of individual stored energies for each system <d-cite key="Niemeyer_JOE1991"></d-cite>.
Therefore, if we assume that the operator and the environment behave passively, the entire system can behave passively if each $n$-port is passive.


			
## E. Stability of Time-delayed Humanoid Robot Teleoperation

Passivity and stability are related as a result of considering the expression of the stored energy as a Lyapunov function <d-cite key="Niemeyer_JOE1991"></d-cite>.
If the $n$-port corresponding to the communication channel is simply determined by a delay, then it can be demonstrated that a pure delay introduces power <d-cite key="Anderson_TAC1989"></d-cite>.
However, it is possible to modify the behavior of the communication channel by using control.
A naive solution is to add damping, but there is no stability guarantee, and it affects the performance <d-cite key="Niemeyer_JOE1991"></d-cite>.
Alternatively, Niemeyer et al <d-cite key="Niemeyer_JOE1991"></d-cite> used the power and energy to define the concept of _wave variables_, where input and output of wave variables are a combination of efforts and flows.
Then, a system is passive if the energy of the output waves is less than the energy of input waves.
In a recent work by <d-cite key="risiglione2021passivity"></d-cite> on bilateral teleoperation of legged robot mobile manipulators, to ensure the passivity and stability they used _energy tanks_ as energy observers and included that as a constraint to the robot whole-body control layer.
The problem is that achieving passivity does not guarantee good performance <d-cite key="Chopra_ACC2003"></d-cite>, and stability and transparency are conflicting objectives <d-cite key="hokayem2006bilateral"></d-cite>.

More specifically to the humanoid robot's unilateral and bilateral teleoperation, the delay is relevant to the robot's balance and velocity. These challenges have not yet been addressed in the literature. However, in many applications the delay is low, hence does not affect highly the robot balance through teleoperation. In the case of large delays, a higher autonomy level for teleoperation is required. In the case of mid-range delay, a commonly used strategy is _move-and-wait_ to overcome the delay problem, however, this reduces the robot velocity and efficiency in task performance. In the case of bilateral teleoperation and manipulation tasks, the use of this approach is highly limited.
With the rise of machine-learning techniques, an envisioning approach to overcome the delay is to use predictive approaches, both from the human and the robot side.
On one hand, the human motion should be predicted and mapped to the robot, and on the other hand, the robot motion and interaction forces with the environment, as well as the stream of the visual feedback, should be predicted and sent to the human operator. 
Finally, to speculate the humanoid robot's balance through teleoperation with a lower level of autonomy, we may consider the human operator, and retargeting and control strategy, all together, as a complex control system to balance the humanoid robot. In this case, disturbances on the robot can be controlled through the whole teleoperation pipeline and human commands.
By speculating on the simplified robot model, i.e., LIPM , studies shows that if the time delay of the system is higher than a critical time delay, the robot destabilizes <d-cite key="milton2009time"></d-cite>. The critical time delay ${\tau}_{c}$ is relevant to the robot CoM height, i.e., ${\tau}_{c} = \beta  \sqrt{\frac{z_0}{g}}$ from Eq. (2). The lower the CoM height, the lower becomes ${\tau}_{c}$.
This is related to the fact that a lower CoM height implies faster dynamics of the LIPM, hence a lower time delay is tolerated to keep the humanoid robot's balance. Here $\beta$ can be related to different parameters such as the human performance, the retargeting and control strategy, and the robot actuators.
