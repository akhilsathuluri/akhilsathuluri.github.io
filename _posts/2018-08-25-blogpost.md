---
layout: post
title: "What's so interesting in a camel standing up?"
date: 2014-04-30
---
This project tries to solve a variant of what is called as the rising camel problem mentioned in [1]. This consists of two parts:

    1. Modeling and performing trajectory tracking (kinematic) by determining pose of the robot by performing the inverse kinematic analysis of the quadruped body.
    2. To solve the energy optimal control problem of such a quadruped


To solve the first problem it is assumed that the robot is in its quadruple stance phase. This means that all the four legs of the quadruped are all touching the fIoor and the robot is stationary. In such a condition the robot can be modeled as a parallel manipulator for analysis.
The model of the robot being considered is as in [2] and is reproduced below.

## INSERT IMAGE


The inverse kinematic analysis was performed and was used to determine the pose of the robot as its eyes (Imaginary. Assumed to be on the mid point of the front side of the body) track a circle. The result is as shown below.

## INSERT VIDEO

The second problem was solved considering only one half of the symmetric body of the quadruped and the case for optimization was to rise from its sitting pose to a standing pose assuming a planar motion under the effects of gravity

Assumptions involved in solving this problem are that:

   1.  The solutions of the joint angle trajectories were approximated using fourth order polynomials
   2.  The integration over the entire interval was approximated using Gausssian Quadratures instead of performing the actual integration over the whole time period of motion

These helped in solving the problem in a practical time spans on a typical laptop and allowed us to iterate quickly. The problem was solved under various parametric conditions to see the response of the manipulator. The following section contains a discussion on all the cases and the corresponding results.

### Simple shooting:
As the first step we trid solving the complete control problem. The dynamics turned out to be too complex to integrate for the whole time period. So to start with and make the problem simple the effects of gravity were ignored. And also a feedback linearized model was considered to solve the energy optimal problem. The solution to this problem is a shown in the video below. It can be seen that the presense of the third actuator in an asymmetric position did not effect the solution at all. The complete motion was symmetric throughout the time. This might be seen that such a model is decoupled as the complex coupling terms are missing which might give some interesting yet incomplete results

## VIDEO

### Without Gravity:
To solve the full problem instead of searching the full space we'll instead approximate the trajectory with a polynomial of fourth order and use a gaussian integration to integrate within the given time interval. This allowed us to practically solve the problem. 

#### Experiment: 
The same construction of the manipulator as shown above was considered andThe problem of raising to a final state was done without considering the effects of the gravity first. The tests were performed parametrically by changing the number of Gauss Quadrature sampling points. The following are the results obtained. The results obtained were different from the one obtained from decoupleing the problem. This confirms the fact that the problem cannot be solved by using simple feedback linearization technique. This decouples the problem loosing valuable trajectories which might exploit the coupled effects in the dynamics.

## VIDEO

### With Gravity:
This deals with the raising camel problem in its full glory. This problem is same as the above but considering the effects of gravity in this case. The test was performed with changing Gauss Quadrature sampling number. The result is as shown. One can see a striking similarity between the optimal solution between this and the camel rising. Though both of them differ in terns of construction, i.e. the number of degrees of freedom and the number of links (bones involved) in a camel a different from experimented case, the solution can be seen very relevant and a similar motion can be observed in the real scenario.

## VIDEO

### Unrealistic Mass Experiment:
 The body link was given a very high mass to see if it could come up with a control strategy to reach the final pose. The following is the result. The result gives us some interesting insights into how the task was solved.

The inspiration for this experiment is this [1] speaking about power lifiting of a load more than the prescribed value by a PUMA robot. We wanted to see if we can observe such joint trajectories to lift a very high body mass.

Initially instead of lifting the link to the final state it lets gravity do the job for it. While transitioning from moving downward to upward it makes sure that the left part of the linkages are aligned such that the load is completely taken by the ground joint so that there is no additional effort by the motors in lifting it up. Before raising itself up, it moves almost in a straight line path, which implies that there is no change in its potential energy throughout that motion.

The manipulator was enforced to reach a ﬁnal end state, so the ﬁnal total energy is the potential energy of all the links only. Since the net energy is the only energy being pumped by the motors, the interest of the motors is to take the body link to the top and hence the energy pumped into the system shouldnt be wasted as potential energy of the system. So the manipulator tries to maintain the body in the horizontal position i.e. no energy is used as potential energy and all the energy pumped in is the kinetic energy of the high massed link. Thus once the transmission angle is optimal the other actuator simply goes to full actuation pushing the link to the ﬁnal state. This explains that horizontal path.

## VIDEO

## **References**:
1. J. E. Bobrow et. al., "Optimal Robot Motions for Physical Criteria", Journ. of Robotic Systems, 2001
2. Jingjun YU, et.al., ”Motion capability analysis of a quadruped robot as a parallel manipulator”, Front. Mech. Eng., 2014
