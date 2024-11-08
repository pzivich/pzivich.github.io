---
layout: page
title: Robins 1986
description: My 2020 reading of Robins 1986.
---

During 2020, I read through Robins, J. (1986). "A new approach to causal inference in mortality studies with a 
sustained exposure period—application to control of the healthy worker survivor effect". *Mathematical modelling*, 
7(9-12), 1393-1512. This was all shared on Twitter. As I deleted my Twitter account long ago now, this thread 
disappeared along with it. To preserve it, I now host it here. 

Below is all from the original 2020 thread. There is likely different elements I would emphasize now, but I leave that
for a future date.

## Setup

Because I have been meaning to read through it fully and this is a better way to keep myself accountable, a thread 
as I (we) read through Robins 1986. (Also writing it out helps me think better)

I will probably do a section every (or every few) day(s)
Some of my nomenclature: 
CI – Causal inference
RR – Risk Ratio
HWE – Healthy worker effect
DAG - Directed Acyclic Graph
LTFU - lost-to-follow-up
RCT - randomized control trial (overlook the 'control' in some of the discussion, I use for ease of abbrev.)
(going to regret not putting more here)


## 1: INTRODUCTION
After 3 pages of vocab and the section it is defined in, we start with the introduction. 

Robins begins with the difficulty of defining an appropriate comparison for a working population, 
since an unexposed* working pop is ‘healthier’ than the general pop

<img align="right" src="../assets/images/robins1986/s1_i1.png" alt="." width="300">

I think most importantly is that Robins sets out to identify ‘small’ effects since most large occupational exposures 
already have been discovered. I think this stands in stark contrast to claims about CI being less appropriate for small 
effects or sensitivity analyses (E-values).

To avoid the HWE, workers with different levels of exposure are compared. However, the standard methods of looking at 
cumulative exposures can mask those small effects Robins is interested in.

<img align="right" src="../assets/images/robins1986/s1_i2.png" alt="." width="300">

To relate to the larger literature, he mentions this paper by Gilbert. This approach is later said to be commonly used 
in occupational epi (at the time).

Gilbert 1982 talks about occupational factors at the Hanford nuclear site on mortality. Gilbert says that differences 
in mortality between employed and terminated works are sources of bias due to the healthy worker effect.

<img align="right" src="../assets/images/robins1986/s1_i3.png" alt="." width="300">
<img align="right" src="../assets/images/robins1986/s1_i4.png" alt="." width="300">

To address this, workers were considered as ‘employed’ up to 3 years after their termination. Gilbert’s approach works 
as a sort of ‘wash-out’ period for occupational exposures. However, Robins says this wash-out approach doesn’t work and 
we will see this in occupational exposure to arsenic. He gives us a teaser (so we get through the following 100+ pages).

<img align="right" src="../assets/images/robins1986/s1_i5.png" alt="." width="300">

Occupational arsenic has been decreased post-1935 but lung cancer has remained elevated among copper smelter workers. 
This could be due to (1) remaining arsenic exposures, or (2) elevated cigarette smoking among workers. Using the 
lagging approach, cumulative exposure to arsenic has no association with lung cancer mortality. However, Robins’ 
proposed approach does find elevated lung cancer mortality. He conjectures that it is due to smokers leaving employment 
more than non-smokers. He can’t directly tell us (so a bit of a letdown).

<img align="right" src="../assets/images/robins1986/s1_i6.png" alt="." width="300">

Robins then says that using the proposed method is necessary because of reduced occupational exposures leading to 
smaller effects (as indicated by RR).

<img align="right" src="../assets/images/robins1986/s1_i7.png" alt="." width="300">

Then he hit us with the succinct purpose of the paper; when do we get to give causal interpretations for time-varying 
exposures with observational data. Robins then outlines what each section will discuss. I won’t repeat / spoil it 
though (but it would be great to do a SPOILER ALERT for a paper that is older than me).

## 2: OBS STUDY AS RCT

