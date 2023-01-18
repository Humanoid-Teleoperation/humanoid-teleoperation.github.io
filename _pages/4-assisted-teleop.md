---
layout: distill
permalink:  /4-assisted-teleop/
title: IV. ASSISTED TELEOPERATION
nav: false
nav_order: 1
description:
date:
bibliography: humanoid-teleoperation.bib

toc:
  - name: 'A. Shared Control'
  - name: 'B. Supervised and Safeguarded Teleoperation'
  - name: 'C. Bilateral Teleoperation'
    subsections:
      - name: '1) Upper-body bilateral teleoperation'
      - name: '2) Whole-body bilateral teleoperation'
  - name: 'D. Impedance Control'
---

In many teleoperation scenarios, controlling the robot as explained in the previous section, is not the only viable solution.
In fact, many tasks can achieve higher performances by sharing the autonomy among the human and robot. This section provides more details about these assisted teleoperation strategies.

## A. Shared Control
Delegating robot's full control to the human operator's experience can often limit the efficiency of the teleoperation, resulting in clunky motions, failures, or numerous attempts before being able to accomplish a given task.
This applies particularly to humanoid robots where the operator has to control many aspects at once via teleoperation (e.g., the pose of both hands, the feet location, balance) and can fail very easily without significant robot autonomy being used simultaneously.
In shared-control teleoperation, some robot autonomy is used to assist the user in accomplishing the desired task, potentially making teleoperation easier and more seamless. Generally, the operator's input is modified according to specific metrics by sharing the control authority between the robot and the operator to enhance performance or safety <d-cite key="dragan2013"></d-cite>. 
For example, in <d-cite key="rakita2019"></d-cite>, Rakita _et al._ teleoperated the upper-body of a humanoid using a shared-control approach, providing on-the-fly assistance to help the user complete tasks more easily, enhancing the end-effectors control while performing bi-manipulation of objects. Similarly, in <d-cite key="rahal2019"></d-cite>,  Rahal _et al._ designed a shared control approach to assist the human operator by enforcing different nonholonomic-like constraints representative of the cutting kinematics. In other shared-control approaches, the user provides an input $\bf{u}$, which enables the robot to predict human intent, and assist her/him in the task by adjusting the motion or by executing a pre-optimized version of that motion <d-cite key="dragan2013"></d-cite>. Then, a blending policy arbitrates the user input $\bf{u}$ and the enhanced robot motion $\bf{r}$, determining the final reference:
\begin{equation}
\bf{u^*} = (1-\alpha)\bf{u}+\alpha\bf{r},
\label{eq:sharedcontrol}
\end{equation}
where $\alpha$ can be any scalar function. A common choice is the confidence in the prediction of the user intent:
\begin{equation}
\alpha = max(0, 1 - d/D),
\label{eq:alpha}
\end{equation}
where $d$ the distance to the goal and $D$ some threshold past
which the confidence is 0. In this case the closer the robot gets to a predicted goal, the more likely that this goal is the correct one, and the input $\bf{r}$ is preferred over $\bf{u}$.
The prediction of the user intent has also been successfully used to provide haptic guidance through a master device to teleoperate a robot manipulator <d-cite key="Ly2021"></d-cite>, and could be applied to humanoid robots by using exoskeletons as input devices. The haptic information can also be used to enhance the user's comfort during teleoperation <d-cite key="Rahal2020"></d-cite>.

## B. Supervised and Safeguarded Teleoperation
When full robot autonomy is available for a given task, the operator can simply act as a supervisor. By monitoring the robot, the operator can then identify and react to unexpected problems and intervene in a timely manner by controlling the robot directly to handle “uncovered” situations. This was a common approach in the DRC, where team operators could guide the robot to achieve complex tasks through failure when needed <d-cite key="johnson2017team"></d-cite>.
Similarly, in <d-cite key="dylan2013"></d-cite>, the user monitored multiple robots interacting with passersby in a shopping mall. The robots performed their own speech, gesture, and motion planning autonomously, and the role of the human was only to provide occasional sensor inputs. In rare cases, an operator had to control the robot directly to handle unexpected questions from a customer or to re-plan the robot’s path to avoid unmodeled obstacles.

A mirrored approach can also be adopted when teleoperating robots. For example, in <d-cite key="fong2001"></d-cite>, the operators shared control with a safeguarding system onboard the robot. In benign situations, the
operator had full control of the vehicle's motion, while in hazardous situations, the safeguarder modified or overrode the operator's commands to maintain safety. The safeguarder, therefore, exhibits many characteristics of autonomous systems, such as perception and command generation. In <d-cite key="fong2001"></d-cite>, the safeguarder not only had the function of preventing collision and rollover but also monitoring the system's health (e.g., vehicle power, motor stall). A similar approach could be used for humanoid robots to prevent them from falling or reaching singular configurations while being operated by the user.

<!-- %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%% ADMITTANCE CONTROL %%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% -->
## C. Bilateral Teleoperation
Bilateral teleoperation techniques have been widely used in the literature for robot manipulators.
In this approach, not only the robot receives kinodynamic references from the human, but the operator also receives kinesthetic feedback (force, pressure, vibration, etc) from the robot. This feedback informs the operator about the robot's performance reproducing the commanded motion or about external disturbances applied to the machine.
The approaches described next focus on teleoperating the upper- or whole-body, which in the latter case couples altogether the human operator and the robot at upper- and lower-body levels.

### 1) Upper-body bilateral teleoperation
A simpler strategy that has been adopted on humanoid robots consists in teleoperating the upper-body in a bilateral fashion, while using a separate balancing controller on the lower-body to regulate balance <d-cite key="brygo2014a,peer2008"></d-cite>. To control the upper limbs of the HRP-2, Peer _et al._ <d-cite key="peer2008"></d-cite> adopted a common control scheme for position-controlled robots: the _admittance_ controller. Such controllers define the reference through the differential equation of a virtual mass-spring-damper system.
Under time delay, the parameters of the controller should be selected appropriately to guarantee stability of the overall teleoperation system, as done in <d-cite key="evrard2009"></d-cite>
while teleoperating the HRP-2 located in Tsukuba (Japan) from Munich (Germany).

### 2) Whole-body bilateral teleoperation
An extension of the conventional idea of bilateral teleoperation is starting to be investigated to dynamically couple human and robot at a whole-body level <d-cite key="ramos2018"></d-cite>. This strategy consists of mapping the whole-body kinematic (joints position, velocitiy, etc) and dynamic (contact forces, joint torques, etc) references from  humans to robots, while providing the operator with feedback regarding the robot's whole-body dynamics, as shown in Fig. 5. However, the naturally unstable dynamics of humanoid robots poses an additional challenge to the whole-body teleoperation: the robot
must balance while reproducing human movement. 

The strategies for whole-body bilateral teleoperation utilize kinesthetic feedback to inform the operator about the robot's dynamics and stability in real-time. The strategy usually focuses on the CoM dynamics, and other condensed information about the robot. For instance, the cable driven feedback interface in <d-cite key="peternel2013"></d-cite> exerts forces on the demonstrator’s waist corresponding to the state of the robot’s CoM. This feedback allows the human to teach the robot how to compliantly interact with the environment. In <d-cite key="Wang2015"></d-cite>, the feedback force applied to the human's torso is proportional to how close the robot is from tipping over. This is estimated by considering the distance between the robot's CoP and the edge of the support polygon. The closer the robot is from tipping over in one direction, the larger the feedback force applied to the operator in the opposite direction. A similar strategy is used in <d-cite key="brygo2014b"></d-cite> by providing discrete vibration levels to the operator using a belt with vibrotactile feedback. In <d-cite key="ishiguro2020bilateral"></d-cite>, the force feedback device TABLIS, a powered exoskeleton, applies forces to the operator's feet to indicate that the robot is stepping onto an obstacle. This enables the operator to control the robot to navigate over objects. Finally, in <d-cite key="ramos2019dynamic"></d-cite> the force feedback is utilized to dynamically synchronize human and machine. The force feedback generates drag (negative feedback) if the robot cannot keep up with the operator's movement, or it speeds up human motion (positive feedback) if the robot moves faster than the operator. The high-level expression for the force feedback is given by:
\begin{equation}
    {\bf{f}_{fb}} = {k_{H}}\left[\left( {\dot{\bf{x}}_R}' - {\dot{\bf{x}}_H}' \right) +  {\bf{f}_{ext}}'\right],
\end{equation}
where $\dot{\bf{x}}_i'$ is the dimensionless CoM velocity of the human ($H$) and robot ($R$) <d-cite key="pratt2006"></d-cite>, $\bf{f}_{ext}'$ is dimensionless external force vector applied to the robot, and $k_H$ is a scaling factor proportional to the operator's size and body mass. This strategy enables human and robot to dynamically take simultaneous steps.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/paper/Bilateral teleoperation.png" title="control-diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig. 5: General concept for whole-body bilateral teleoperation. The robot  WBC computes joint torques $\tau_{j}$ using the reference interaction forces $F_H$ from the operator and the error $e$ between the human state $X_H$ and the robot state $X_R$. The external contact forces $F_k$ applied to the robot create a net wrench $W_{ext}$, which is used by the human-machine interface (HMI) to compute a proportional kinesthetic feedback $F_{fb}$ to the operator.
</div>

<!-- 
\begin{figure}[!t]
  \setlength\belowcaptionskip{-0.7\baselineskip}

    \centering
    \includegraphics[width=2.5in]{Figures/Bilateral teleoperation.png}
    \caption{
    General concept for whole-body bilateral teleoperation. The robot  WBC computes joint torques $\tau_{j}$ using the reference interaction forces $F_H$ from the operator and the error $e$ between the human state $X_H$ and the robot state $X_R$. The external contact forces $F_k$ applied to the robot create a net wrench $W_{ext}$, which is used by the human-machine interface (HMI) to compute a proportional kinesthetic feedback $F_{fb}$ to the operator. 
    }
    \label{fig:Bilateral_Teleoperation}
\end{figure} -->

In general, during whole-body bilateral teleoperation, the kinesthetic feedback provided to the operator is proportional to some kinematic or dynamic discrepancy between human and robot with respect to the task at hand and/or the balance regulation. The assisted teleoperation principle arises from the fact that the robot must prioritize between following the human motion command to perform a task and maintain its own bipedal stability. Some strategies shift the balancing authority to the robot's autonomous controller. This means that the robot is responsible for predicting if a given command will jeopardize stability and deciding the best course of action to override the motion. For instance, in <d-cite key="ishiguro2018"></d-cite>, the robot's controller uses stability considerations from the LIP model to modify the CoM trajectory commanded by the human, preventing the operator from destabilizing the robot. This represents a more conservative approach that guarantees stability of the movement of the robot, but prevents the operator from exploring motions that would go beyond the boundaries of the stability metric employed. In contrast, other approaches, such as <d-cite key="Ramos_Humanoids2015"></d-cite>, rely on the human operator to actively regulate the robot's balance. 
In this sense, the robot follows the human's movement with only minor regulation from the robot's autonomous controller; then,
the operator must perceive the robot's destabilization through the kinesthetic feedback and mitigate it by adapting the commanded movement. Although riskier, this strategy frees the operator from abiding to the boundaries of predefined stability metrics, which are challenging to be mathematically defined in the context of legged robots. The goal of this approach is to eventually allow the operator to learn how to cope with the robot's dynamics and to create new motions on the fly. 

## D. Impedance Control
A similar concept to admittance control can be employed in non-bilateral systems to provide the robot the ability to dexterously interact with the remote environment. In <d-cite key="brygo2014a"></d-cite>, Brygo _et al._ implement an autonomous _impedance_ controller that regulates the robot’s joints stiffness and damping according to the manipulation loading conditions. Also in this case a virtual mass-spring-damper system is employed, but the main difference between admittance control and impedance control is that the former controls motion after a force is measured, while the latter controls force after motion (or deviation from a set point) is measured <d-cite key="keemink2018"></d-cite>. In <d-cite key="brygo2014a"></d-cite>, the COMAN robot performs free-space motions with compliant limbs to ensure safe interactions during unforeseen collisions on the whole-arm. During the manipulation task, the controller stiffens the humanoid arm joints according to the the external force sensed at the end-effector, permitting to handle the task loads.

Alternatively, the impedance profile can be sent to the robot through a BMI applied to the operator's arm, using for example non-intrusive position and  EMG measurements, technique also known as _tele-impedance_ <d-cite key="ajoudani2012"></d-cite>.

