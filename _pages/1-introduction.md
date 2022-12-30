---
layout: distill
permalink: /1-introduction/
title: I. INTRODUCTION
nav: false
nav_order: 1
description:
date:

# authors:
#   - name: Albert Einstein
#     url: "https://en.wikipedia.org/wiki/Albert_Einstein"
#     affiliations:
#       name: IAS, Princeton
#   - name: Boris Podolsky
#     url: "https://en.wikipedia.org/wiki/Boris_Podolsky"
#     affiliations:
#       name: IAS, Princeton
#   - name: Nathan Rosen
#     url: "https://en.wikipedia.org/wiki/Nathan_Rosen"
#     affiliations:
#       name: IAS, Princeton

bibliography: 2018-12-22-distill.bib

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
# toc:
#   - name: Equations
#     # if a section has subsections, you can add them as follows:
#     # subsections:
#     #   - name: Example Child Subsection 1
#     #   - name: Example Child Subsection 2
#   - name: Citations
#   - name: Footnotes
#   - name: Code Blocks
#   - name: Layouts
#   - name: Other Typography?

# Below is an example of injecting additional post-specific styles.
# If you use this post as a template, delete this _styles block.
# _styles: >
#   .fake-img {
#     background: #bbb;
#     border: 1px solid rgba(0, 0, 0, 0.1);
#     box-shadow: 0 0px 4px rgba(0, 0, 0, 0.1);
#     margin-bottom: 12px;
#   }
#   .fake-img p {
#     font-family: monospace;
#     color: white;
#     text-align: left;
#     margin: 12px 0;
#     text-align: center;
#     font-size: 16px;
#   }

---


There are many situations and environments where we need robots to replace humans at the site.
Despite the recent progress in robot cognition based on AI techniques, fully autonomous solutions are still far from producing socially and physically competent robot behaviors; that is why teleoperating robots (Fig. 1) acting as physical avatars of human workers at the site is the most reasonable solution.
In environments like construction sites, chemical plants, contaminated areas and space, teleoperated robots could be extremely valuable, relieving humans from any potential hazard.
Contrary to other conventional robotic platforms, humanoids' structure is a better fit for environments and tasks that are designed for and performed by humans. The operational versatility of these robots makes them suitable for work activities that require a variety of complex mobility and manipulation skills, such as inspection, maintenance, and interaction with human operators.
In certain contexts such as telenursing, where human subjects are expected to interact with a teleoperated robot, the human-likeness factor is important since it increases the acceptability, social closeness, and legibility of its intentions <d-cite key="dragan2013a"></d-cite>.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/paper/intropic.png" title="intro pic" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Fig 1: Examples of humanoid robot teleoperation; from top left to bottom right corner: <d-cite key="ramos2018"></d-cite>, <d-cite key="darvish2019"></d-cite>, <d-cite key="penco2019"></d-cite>, <d-cite key="ishiguro2020bilateral"></d-cite>, <d-cite key="jorgensen2019"></d-cite>, <d-cite key="abi2018"></d-cite>, <d-cite key="kim2013"></d-cite>, <d-cite key="Cisneros2022Team"></d-cite>.
</div>


In the literature, different attempts have been made to
> deploy the senses, actions, and presence of a human to a remote location in real-time, leading to a more connected world <d-cite key="AnaAvatarXprize"></d-cite>.

Inspired by a visit to the Tachi Lab, the XPRIZE Foundation has recently launched the ANA Avatar XPRIZE global competition <d-cite key="AnaAvatarXprize"></d-cite>.
Previously, in response to the 2011 Fukushima Daiichi nuclear disaster, the DARPA Robotics Challenge (DRC) was launched to promote innovation in human-supervised robotic technology.
In space applications, rovers and mobile manipulators were teleoperated from aboard the International Space Station (ISS), in the context of METERON and Kontur-2 projects <d-cite key="kontur-meteron"></d-cite>. In 2019, the humanoid Skybot F-850 was rocketed to the ISS <d-cite key="skybot2019"></d-cite>; however, it turned out to have a design that did not work well, demonstrating that there is still work to do to get humanoids into space.


<!-- % challenegs -->
Humanoid robot teleoperation involves many multidisciplinary and interleaved challenges, ranging from dynamics and control to communication and human psychophysiology. Uniquely, due to their resemblance to human appearance, societal expectations are high as well;
they are expected to do a wide range of tasks that are not expected from other types of robots. They are highly redundant with nonlinear, hybrid, and underactuated models.
While doing dynamic and agile motions with the feet like walking, running, or stepping over obstacles, they are supposed to perform dexterous power and precision manipulation.
At the same time,
they are expected to work alongside humans, be safe, friendly, and socially interact with others.
On the other hand, teleoperation interfaces and techniques should be designed such that the human operator receives minimal, effective, and informative haptic feedback from the humanoid robot, to cover for human errors, overcome communication delays, and above all, be telepresent. Along with these challenges, the field is new and due to its high resource demand for development, not many laboratories have been working on it.

<!-- % comparison -->
Many efforts from the robotics community have been devoted to studying humanoid robots, teleoperation, evaluation metrics, or human-robot interaction.
Among them, the book on humanoid robotics <d-cite key="goswami2019humanoid"></d-cite> studied comprehensively different aspects of humanoid robots, including their history, design, mechanics, control, simulation, and interaction. 
Several survey papers likewise studied specific aspects of humanoid robots, for example humanoid dynamics <d-cite key="sugihara2020survey"></d-cite>, control <d-cite key="yamamoto2020survey"></d-cite>, motion generation <d-cite key="Tazaki2020survey"></d-cite>, or robot teleoperation interface design and metrics <d-cite key="de2009survey"></d-cite>.
A primary work on bilateral teleoperation techniques has been presented by <d-cite key="hokayem2006bilateral"></d-cite> as well. 
Another seminal survey <d-cite key="Goodrich2007Survey"></d-cite> covers many aspects of interactive robots, including their design, autonomy level, and human factors that helped us in articulating the current manuscript.
Another interesting survey <d-cite key="goodrich2013teleoperation"></d-cite> highlights several aspects of humanoid teleoperation and autonomy.
However, <d-cite key="goodrich2013teleoperation"></d-cite> is a decade old, and an up-to-date survey on the topic is missing, especially considering that humanoid teleoperation is a far-from-solved challenge and a highly active field of research where new solutions are proposed each year.
Following the workshop in <d-cite key="workshop2019"></d-cite>, this survey paper presents the latest results in humanoid robot teleoperation and draws in detail the challenges that the research community faces to effectively deploy such systems toward real-world scenarios.



Starting from what emerged from the workshop, we conducted a survey on teleoperation of humanoid robots. We present here the systems and devices that have been adopted so far to teleoperate humanoids (Sec. \ref{sec:TeleoperationSystemDevices}) and how these robots have been modeled, retargeted, and controlled (Sec. \ref{sec:RobotControl}). We also examine a
promising case of teleoperation in which the robot assists the user in accomplishing a desired task (Sec. \ref{sec:AssistedTele}). 
Later, we discuss complications along with some compensating solutions that arise due to non-ideal communication channels (Sec. \ref{sec:CommunicationChannel}).
We explain the evaluation of teleoperation systems prior to development to meet the users' needs (Sec. \ref{sec:EvaluationMetrics}). 
Finally, discussions on current and potential applications and the associated challenges follow (Sec. \ref{sec:Applications}).  
