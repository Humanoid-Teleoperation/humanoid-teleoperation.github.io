---
layout: distill
permalink:  /7-applications/
title: VII. APPLICATIONS & PERSPECTIVES
nav: false
nav_order: 1
description:
date:
bibliography: humanoid-teleoperation.bib

toc:
  - name: 'A. Telexistence and Telepresence'
  - name: 'B. Teleoperation in Hazardous Environments'
  - name: 'C. Teleoperation in Manufacturing and Research Environments'
  - name: 'D. Telenursing'
  - name: 'E. Space Applications'
  - name: 'F. Service Robotics Application'
---


Future applications of teleoperated humanoid robots are very promising but further progress is required to employ these robots in real world scenarios. 
For successful teleoperation, the theoretical foundations are provided in the previous sections.
Here, we overview major applications of the humanoid robot teleoperation, and discuss their challenges and opportunities.

## A. Telexistence and Telepresence
The COVID-19 pandemic has either canceled many conferences and meetings around the world or led them to be transformed into virtual events.
Moreover, many people cannot see their beloved ones frequently. The current substitution for such cases currently is to use communication mediums, allowing the people to see and hear each other. However using these means, many social cues -equally important in social interaction- are not yet conveyed. Instead, humanoid robot teleoperation with anthropomorphic shape and motion, similar to a human, would allow for a better experience. Moreover, it would allow people to interact physically with each other.
Currently, the ANA Avatar XPRIZE competition <d-cite key="AnaAvatarXprize"></d-cite> is aiming at this application. 
The main challenges in this context are to allow the operator and the humans who interact with the robot to engage in a scenario, feel the presence of the operator, and enable manipulation in the remote environment.

## B. Teleoperation in Hazardous Environments
One of the main applications urging robot teleoperation is in disaster-response scenarios where the environment is potentially hazardous to humans.
This need arose, for example, in the Chernobyl and Fukushima Daiichi Nuclear Power Plants crises <d-cite key="nagatani2013emergency"></d-cite>. As a response to these disasters, robots were needed to perform surveillance, search and rescue, and manipulation tasks. 
However, to do that, a robot should reach the point of interest passing possibly through a dynamic and unstructured environment to perform a given task.
Bipedal locomotion overcomes other locomotion means in terms of mobility, agility, and a wide range of motion of the robot; therefore, reliable humanoid robot teleoperation can assist the human in such cases.
In these scenarios, the mission requirements allow to identify necessary robot features such as hardware reliability, communication protocols, additional hardware and sensors, autonomy level, and so on.
Normally, in natural disasters the time is very critical; therefore, another important aspect
to consider
is the response time and the technology readiness level. For example, in the Fukushima 
crisis where the human could not enter because of the radiation levels, it took more than three months to deliver a robot that could perform the first mission <d-cite key="nagatani2013emergency"></d-cite>. However, in cases such as Urban Search and Rescue Tasks, where humans' lives are jeopardized, 
the delay for intervention is not admissible~<d-cite key="casper2003human"></d-cite>.

## C. Teleoperation in Manufacturing and Research Environments
Humanoid robots, despite being attractive because of their anthropomorphism and potential to operate in environments designed for humans, are still expensive and not affordable for many industries and research institutes.
So far, this inconvenience has strongly limited their study to a restricted robotics community.
Moreover, very often either the robot hardware or the underlying control software (or both) are not designed to comply with control failures, loss of balance or wrong interactions with the environment, which can lead to costly breakage. 
In an example of teleoperation in a manufacturing environment by Kheddar et. al. by <d-cite key="kheddar2019humanoid"></d-cite>, the humanoid robots TORO and HRP-4 have been deployed in an aircraft manufacturing environment for assembly operations.
Another example in construction sites can be found in~<d-cite key="yokoi2003tele"></d-cite>.


## D. Telenursing
Front-line healthcare workers are exposed to infectious diseases and are at higher risk of infection compared with the general community. This was evident during disease outbreaks, as experienced during the recent COVID-19 pandemic.
Nurses physically interact with their patients and the environment for a wide variety of tasks such as manipulating objects, taking measurements, and interacting with them.
In this respect, teleoperated robots can facilitate the situation and improve the nurses' safety by performing some of their tasks, exemplified in~<d-cite key="li2017development"></d-cite>.
However, robots should not only perform the nurses' tasks but also avoid patients' discomfort or avoid limiting other health worker activities.
In this respect, the teleoperation of humanoid robots can potentially overcome these challenges when being deployed in clinical environments with the supervision of professional operators and other healthcare personnel.



## E. Space Applications
Space robotics has many applications, including satellite on-orbit servicing, maintenance of the ISS, performing experiments there, and interplanetary exploration and construction~<d-cite key="workshop2019, flores2014review"></d-cite>.
Some of these tasks cannot be performed by humans due to cost, safety, and the increased complexity of the required system. 
On the other hand, the reliability and robustness of autonomous robots are not yet sufficient to perform such tasks autonomously. Therefore, teleoperation of space robots with different degrees of autonomy is required.
Space applications are more challenging due to communication latency and bandwidth, possible unknown kinematics and dynamics properties of the target objects of manipulation, and human factors~<d-cite key="flores2014review"></d-cite>.
In the case of bilateral teleoperation, the round trip communication delay matters; however, time-domain passivity control approaches can compensate to some extent for earth-orbiting robots with the cost of degrading the efficiency <d-cite key="ryu2010passive"></d-cite>.
However, for application with higher distances, it is a compromise between autonomy, risk, and efficiency.
To overcome that, <d-cite key="Lii2017Toward"></d-cite> proposed a supervised autonomy framework with a natural interface to astronauts in the ISS for teleoperating the SUPVIS Justin robot on Earth, simulating an interplanetary solar panel service and maintenance task.


## F. Service Robotics Application
Another area of use of humanoid robot teleoperation is in domestic environments such as houses,
supermarkets, schools, and hotels with a diverse range of goals such as giving care to elderly people or housekeeping~<d-cite key="broekens2009assistive"></d-cite>, restocking the market shelves,
teleducation, guiding visitors in hotels, or teletourism. 
These environments are intrinsically unstructured and built for humans' use; therefore, a humanoid robot is likely to be deployed for such applications.
These applications will become more evident when the operator of the humanoid robot cannot be present in the target environment. In other words, workforces who teleoperate the humanoid robot can be at any place.
The main requirements for such applications to be acceptable are the safety of humanoid robots with the people whom they are interacting with, and the ability to manipulate and modify remote locations.
