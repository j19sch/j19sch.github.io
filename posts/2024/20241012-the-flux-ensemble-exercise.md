<!--
.. title: The Flux ensemble exercise
.. slug: the-flux-ensemble-exercise
.. date: 2024-10-13
.. category: 
.. tags: 
.. type: text
.. description: The Flux ensemble exercise is an exercise in working in an ensemble, where the navigator can add or remove rules for the ensemble. The goal of the exercise is to experience why the basic rules of ensembling are the way they are and what happens if they are different.
-->

Last week I ran a full-day workshop at HUSTEF on working in an ensemble (aka mob programming/testing or software teaming). As part of the workshop I tried out a new exercise, in which participants were allowed to change the rules of the ensemble. The goal was to experience why the basic rules of ensembling are the way they are and what happens if they are different.

Since the participants really liked the exercise, I figured I'd write about it and name it: the Flux ensemble exercise. For those not familiar with Flux: it is a card game in which changing the rules is a key part of the game. It's a lot of fun.

<!-- TEASER_END -->

# The basic of rules of ensembling {.small}

When I run an ensembling workshop, I like to put the basic rules on a flipchart (credit to Lisi Hocke for the inspiration):

<!-- todo: add image -->

I am not going to explain the whole set of rules, I'll limit myself to the ones relevant to describe how the exercise went during the workshop.

## The roles
There are four roles in an ensemble: facilitator, driver (hands), navigator (brain), and passengers (voices).

The facilitator is exactly that: they don't participate, they only guide the ensemble when needed. 

The driver (hands) is the person sitting behind the computer. They turn the computer in an intelligent input device. In essence (although there is some nuance to it) they do as they are told by the navigator.

The navigator (brain) is the person making the decisions on what to do next. They listen to what the passengers (voices) say, communicate to the rest of the ensemble what's the next thing they want to achieve, and they give instructions to the driver (hands).

The passengers (voices) share their observations and ideas with the navigator (brain). This can either happen out of their own accord, or because the navigator (brain) actively asked for their input.


## The rotation
Every few minutes the people in the ensemble (driver, navigator, passengers) rotate through the roles. I prefer to have the navigator become the driver, the driver a passenger, and a passenger to become the new navigator. Reason for that is that it makes it very clear to the navigator that they are no longer the navigator. They no longer make the decisions (navigator), nor provide input for the decisions (passengers). They are there to execute the decisions (driver).

For the duration of the rotations 3 minutes works well. It's long enough to accomplish something and short enough that the new navigator needs to continue the thread of the previous one. The duration of the rotations is one of the counter-intuitive aspects of ensembling. People who haven't participated in an ensemble often want to make the rotations longer, while as a general rule shorter is actually better.


## What the rules are meant to achieve
The rules of ensembling are meant as forcing functions or enabling constraints. They don't exist for their own sake, they are meant to make something happen. And every ensemble I've ever facilitated quite quickly starts to loosen up the rules a bit. Most of the time in a good way, because they do have the rules in the back of their minds. And that's where the best ensembling happens: in the grey area where you don't always follow the letter of the rules, but you do follow their intent. It's also what makes facilitating an ensemble both fun and intersting each time.

Good ensembling means that everyone is on the same page about what the next thing is the ensemble wants to achieve. There might be differences to what degree every member in the ensemble knows how to achieve it, though. That's fine, because that's the strength of an ensemble. You get something done as a group, with every participant either contributing or learning


# The Flux ensemble exercise {.small}

use the flip chart with rules in play at the top, potential changes at the bottom


# The rules we changed during the workshop {.small}

target: parking calculator, exploratory testing

13 ideas brainstormed

some mutually exclusive, so pay attention to correctly update rules in play

## Brainstormed but not used
- 2 drivers (both projected, e.g. doing and note-taking)
- fixed roles
- navigator decides when to rotate
- facilitator picks driver/navigator
- navigator is the driver
- time +


## Used
- no navigator
	- worst
	- could be worse
	- too comfortable
	- chaos
- passengers only talk when asked
	- dislike
	- killed dynamic
	- I have an idea!
- time - (rotation of 2 mins instead of 3, chosen by navigator)
	- navigator handover
	- too short
	- liberating (less need to do all things thought of)
- rotate at end of action
	- focus
	- express intent
	- bug outside of intent
- finish action when timer goes
	- action boundaries
	- kills 3 minutes
	- risk of discussion
- idea -> navigator
	- how decide when to change?
	- size of an idea
	- me later: easier for programming, i.e. sequence of steps
- 30 sec warning before end of rotation
	- ok