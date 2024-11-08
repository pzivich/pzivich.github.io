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
* CI – Causal inference
* RR – Risk Ratio
* HWE – Healthy worker effect
* DAG - Directed Acyclic Graph
* LTFU - lost-to-follow-up
* RCT - randomized control trial (overlook the 'control' in some of the discussion, I use for ease of abbrev.)

(going to regret not putting more here)


## 1: INTRODUCTION
After 3 pages of vocab and the section it is defined in, we start with the introduction. 

Robins begins with the difficulty of defining an appropriate comparison for a working population, 
since an unexposed* working pop is ‘healthier’ than the general pop

![Screenshot1](../assets/images/robins1986/s1_i1.png)

I think most importantly is that Robins sets out to identify ‘small’ effects since most large occupational exposures 
already have been discovered. I think this stands in stark contrast to claims about CI being less appropriate for small 
effects or sensitivity analyses (E-values).

To avoid the HWE, workers with different levels of exposure are compared. However, the standard methods of looking at 
cumulative exposures can mask those small effects Robins is interested in.

![Screenshot2](../assets/images/robins1986/s1_i2.png)

To relate to the larger literature, he mentions this paper by Gilbert. This approach is later said to be commonly used 
in occupational epi (at the time).

Gilbert 1982 talks about occupational factors at the Hanford nuclear site on mortality. Gilbert says that differences 
in mortality between employed and terminated works are sources of bias due to the healthy worker effect.

![Screenshot1](../assets/images/robins1986/s1_i3.png)

![Screenshot1](../assets/images/robins1986/s1_i4.png)

To address this, workers were considered as ‘employed’ up to 3 years after their termination. Gilbert’s approach works 
as a sort of ‘wash-out’ period for occupational exposures. However, Robins says this wash-out approach doesn’t work and 
we will see this in occupational exposure to arsenic. He gives us a teaser (so we get through the following 100+ pages).

![Screenshot1](../assets/images/robins1986/s1_i5.png)

Occupational arsenic has been decreased post-1935 but lung cancer has remained elevated among copper smelter workers. 
This could be due to (1) remaining arsenic exposures, or (2) elevated cigarette smoking among workers. Using the 
lagging approach, cumulative exposure to arsenic has no association with lung cancer mortality. However, Robins’ 
proposed approach does find elevated lung cancer mortality. He conjectures that it is due to smokers leaving employment 
more than non-smokers. He can’t directly tell us (so a bit of a letdown).

![Screenshot1](../assets/images/robins1986/s1_i6.png)

Robins then says that using the proposed method is necessary because of reduced occupational exposures leading to 
smaller effects (as indicated by RR).

![Screenshot1](../assets/images/robins1986/s1_i7.png)

Then he hit us with the succinct purpose of the paper; when do we get to give causal interpretations for time-varying 
exposures with observational data. Robins then outlines what each section will discuss. I won’t repeat / spoil it 
though (but it would be great to do a SPOILER ALERT for a paper that is older than me).

## 2: OBS STUDY AS RCT

This section is probably one of the most important insights, framing observational data as a randomized trial conducted 
by nature (I think I might like causal inference as a missing data problem more though).

![Screenshot1](../assets/images/robins1986/s2_i1.png)

We start with an example. To add, I am going to adapt a quick example to illustrate his previous point regarding 
‘small effects’ from Section 1 to highlight the importance of his previous argument. Pictured is a DAG for a data 
generating mechanism and some Python code.

![Screenshot2](../assets/images/robins1986/s2_i2.png)

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from zepid.causal.causalgraph import DirectedAcyclicGraph

# Drawing a DAG
dag = DirectedAcyclicGraph(exposure=r"$$A_1$$", outcome=r"$Y$")
dag.add_arrows(((r"$A_1$", r"$Y$"),
                (r"$A_2$", r"$Y$"),
                (r"$A_1$", r"$A_2$"),
                (r"$A_1$", r"$U$"),
                (r"$U$", r"$A_2$")))
dag.draw_dag(fig_size=(6, 4),
             positions={r"$A_1": (1, 1),
                        r"$A_2": (3, 1),
                        r"$U": (2, 1.05),
                        r"$Y": (4, 1)})
plt.show()

# Generating data
np.random.seed(1986)
n = 1000000

# Defining potential outcomes
df = pd.DataFrame()
df['y_a0a0'] = np.random.binomial(n=1, p=0.4, size=n)
df['y_a1a0'] = np.random.binomial(n=1, p=0.45, size=n)
df['y_a0a1'] = np.random.binomial(n=1, p=0.55, size=n)
df['y_a1a1'] = np.random.binomial(n=1, p=0.6, size=n)

# Alloting treatments
df['A_1'] = np.random.binomial(n=1, p=0.5, size=n)
df['U'] = np.random.binomial(n=1, p=0.2 + 0.4*df['A_1'], size=n)
df['A_2'] = np.random.binomial(n=1, p=df['A_1']*0.85 +
                                      (1-df['A_1'])*0.15 -
                                       0.1*df['U'], size=n)

# Applying causal consistency
df['Y'] = (df['A_1']*df['A_2']*df['y_a1a1'] + 
           (1-df['A_1'])*df['A_2']*df['y_a0a1'] + 
           df['A_1']*(1-df['A_2'])*df['y_a1a0'] + 
           (1-df['A_1'])*(1-df['A_2'])*df['y_a0a0']) 
```

Since $A$ is randomized at baseline ($t_1$), we can easily estimate $\Pr(Y(a_1))$ with $\Pr(Y \mid A_1=a_1)$ where 
$Y(a_1)$ is the potential outcome under $a_1$. In my example $\hat{\Pr}(Y \mid A_1=1) / \hat{\Pr}(Y \mid A_1=0)$ is

```python
# Calculating Risk Ratio
from zepid import RiskRatio

rr_est = RiskRatio()
rr_est.fit(df, exposure='A_1', outcome='Y')
rr_est.summary()

# RiskRatio  SD(RR)  RR_LCL  RR_UCL
#     1.354   0.002   1.349    1.36
```

However, I am using 1mil observations for that estimate. That’s probably more than we have in most scenarios. Under the 
more realistic case of 750 observations, things are less clear.

```python
rr_est = RiskRatio()
rr_est.fit(df.sample(n=750), exposure='A_1', outcome='Y')
rr_est.summary()

# RiskRatio  SD(RR)  RR_LCL  RR_UCL
#     1.172   0.074   1.014   1.355
```

Since we are using some simulated data, we can check another estimand $\Pr(Y(a_1, a_2))$. For cumulative effects (i.e., 
effect is monotonic over time), $\Pr(Y(a_1, a_2)) \ge \Pr(Y(a_1))$. This means we have a better chance of identifying 
‘small effects’ of $A$ by targeting $\Pr(Y(a_1, a_2))$.

```python
# Calculating Pr(Y(a_1, a_2)_ directly
print(np.mean(df['y_a1a1']) / np.mean(df['y_a0a0']))
# RiskRatio
#     1.502
```

However, using $\Pr(Y \mid A_1=a_1, A_2=a_2))$ doesn’t correctly estimate the previous quantity because of the $U$ I 
drew in the previous DAG. That’s why we need this paper and the proposed method.

Already we are given a glimpse of what Robins is talking about when he talks about using time-varying exposures to 
identify effects. Returning to Robins example, he gives us this nice tree ($G_m$ is moderate exposure)

![Screenshot3](../assets/images/robins1986/s2_i3.png)

He gives us a table based on some categorizations of the exposures (I have an updated table below). As seen, high 
exposure seems protective. However, we know this isn’t true (the exposure has no effect).

|  | High | Moderate | Low |
| --- | :---: | :---: | :---: |
| Events | 60 | 160 | 100 |
| Total | 200 | 400 | 200 |
| Risk | 0.3 | 0.4 | 0.5 |
| Risk Ratio | 0.6 | 0.8 | 1 |

Rather it is a result of the exposure being an irritant and resulting in unhealthy individuals quitting work earlier 
than healthy individuals.

Robins mentions in this section, if we had treated the baseline assignment of exposure categories (high vs medium) at 
$t_1$, we would correctly have estimated no effect: $RR = (160/400) / (160/400) = 1.0$

![Screenshot4](../assets/images/robins1986/s2_i4.png)

We see how to foundation of observational studies as a randomized trial. Our collaborator, Dr. Nature, isn’t always the 
most organized and seemingly forgets to forward the randomization protocol to us. A primary challenge is determining 
when we consider an individual to deviate from their assigned protocol.

![Screenshot5](../assets/images/robins1986/s2_i5.png)

![Screenshot6](../assets/images/robins1986/s2_i6.png)

Robins states if we (accurately) measure day of death, exposure history, date of leaving the exposure protocol, then we 
can estimate mortality. The trick for translating obs. data into this is to determine when individuals leave the 
protocol.

A related issue (one-sample rather than the two-sample problem Robins is addressing) is when to consider someone as 
censored (LTFU). @leskocar  et al. has a nice discussion of when we should consider someone as censored.

For Robins’ example date of termination of employment works well as the time of deviation from protocol. He also tells 
us a similar exposure protocol end date for the mining industry.

The technical note simplifies the examples being discussed by simplifying the protocol. When we get to section 10, we 
will see how we can have more complex exposure plans (eg work every other year).

![Screenshot7](../assets/images/robins1986/s2_i7.png)

We get some notation: $G(t)$ is the projected exposure history and $E(t)$ is the observed exposure history. In other 
words $G(t)$ is the assigned RCT assigned protocol up to t and the $E(t)$ is the actual exposures.

![Screenshot8](../assets/images/robins1986/s2_i8.png)

2C.1 is treatment-variation-irrelevance, 2C.2 simplifies our problem (and we will relax it in section 10), 2C.3 removes 
more complex exposure plans that depend on measures at $t$.

![Screenshot9](../assets/images/robins1986/s2_i9.png)

The first sentence requires that the past exposure cannot be determined by future events (something we assume 
impossible about reality, but can accidentally do in analyses).

![Screenshot10](../assets/images/robins1986/s2_i10.png)

![Screenshot11](../assets/images/robins1986/s2_i11.png)

Imposing that time-order is for the 3 assumptions, which allows us to freely condition on $G$ (the projected exposure 
history). The individual-level assumptions imply the truth of the population-level versions.

![Screenshot12](../assets/images/robins1986/s2_i12.png)

![Screenshot13](../assets/images/robins1986/s2_i13.png)

In our hypothetical trial on employment termination, the protocol cannot be influenced by unmeasured risk factors 
(randomization is used to make this true).

![Screenshot14](../assets/images/robins1986/s2_i14.png)

Under these conditions, we can consistently estimate survival without the actually assigned protocols! We only need 
the observed exposure history and when the protocol was terminated.

![Screenshot15](../assets/images/robins1986/s2_i15.png)

Robins gives a proof of this by showing the exclusive ways individual $i$ can survive to $t$ -- survive on protocol to 
$t$, terminate protocol at $t-1$ and survive to $t$.

Interestingly, even if we did have information on the assigned protocol, it won’t provide any additional information. 
We could ignore it even if we had it.

This is only a cursory glance at his proofs (I need to work through them but the thread will be insanely long if I do 
here).

Now we can think about RCT where exposure is randomly assigned at t based only on previous exposure history. So we may 
no longer have a well-defined treatment plan at baseline.

![Screenshot16](../assets/images/robins1986/s2_i16.png)

This alt-RCT is a special case of the previous RCT! Specifically in which we don’t get to see the exposure protocol.

![Screenshot17](../assets/images/robins1986/s2_i17.png)

Robins concludes the section with mention that survival is a function of time and exposure can be beneficial / harmful 
at certain times (ie the stratified survival curves are allowed to cross).

![Screenshot18](../assets/images/robins1986/s2_i18.png)

We end this section with knowledge that we don’t need the exposure protocol to analyze our RCT. Now the question is 
when does obs. data reflect a RCT (or rather under what assumptions)

## 3. GRAPHS FOR CAUSAL INFERENCE

