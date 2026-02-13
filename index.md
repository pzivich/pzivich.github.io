---
layout: page
title: Paul Zivich
description: Personal site for Paul Zivich
---

# About

<img align="right" src="assets/images/pzivich_headshot_2023.jpg" alt="Me" width="300">

Dr. Paul Zivich is a research assistant professor in the Department of Epidemiology at University of North Carolina at 
Chapel Hill. His interests are cover quantitative epidemiologic methods development and their practical application to
critical public health questions. The main focus of his work is in causal inference with potential outcomes, infectious 
disease prevention, pharmacoepidemiology, and computational aspects of epidemiology. His work has ranged from assessing 
the performance of estimators through simulation studies to free and open source software (FOSS) to collection of 
contact network data with electronic sensors to application of causal inference in the context of infectious disease 
and social epidemiology.

Paul received his PhD in epidemiology from University of North Carolina at Chapel Hill, and his MPH in 
epidemiology from The Ohio State University. He was born, is conducting research, and will die.

------------------

This website highlights select aspects of my work, software I have written, and other asides. For a full 
summary of my previous work, please see my CV below.

## Navigation

- [Curriculum Vitae](https://pzivich.github.io/assets/cv/pzivich_CV.pdf)
- [Select Publications](pages/publications.html)
- [Select Presentations](pages/presentations.html)
- [Software](pages/software.html)
- [Python Guide](pages/python_intro.html)
- [My Philosophy](pages/philosophy.html)
- [AI Manifesto](pages/ai-manifesto.html)

To adhere to the FAIR (Findability, Accessibility, Interoperability, and Reuse) principles for my research software, 
code from selected publications is available on [Zenodo](https://zenodo.org/record/8100058). For reproducibility, I strive to have aspects of my 
research work double-coded. Many of my projects have code available in at least two programs (generally, Python with 
either accompanying SAS or R code). A special thank you to my co-authors who make this possible.

## Explainers

A collection of previous explainers I have done

- [Robins 1986](pages/robins86.html)
- [Tree Graphs](pages/treegraphs.html)

------------------

## Current Research

The following is a brief summary of my ongoing research projects or current research interests.

### Non-standard causal inference

When first taught causal inference, many associate the framework directly with rote memorization of the standard 
identification assumptions: causal consistency, exchangeability, and positivity. Others associate it with specific 
estimators (e.g., inverse probability weighting). However, causal inference is so much more. I personally view it as a
way to reason about the world that has application to learning from any sort of data (or information).

To showcase this aspect, a major area of my research is in what I will refer to as 'non-standard' causal inference. 
This work is meant to go beyond the basic assumptions and estimators. My work in this area includes
[synthesis modeling](https://arxiv.org/abs/2303.01572) to address violations of the positivity assumption, 
use of [proximal causal inference](https://academic.oup.com/aje/advance-article/doi/10.1093/aje/kwad077/7098281) to 
account for unmeasured confounding variables, 
[data fusion](https://pubmed.ncbi.nlm.nih.gov/39218437/) to integrate information across data sources, 
[machine learning](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8012235/) to weaken modeling assumptions, 
and [causal inference with interference](https://onlinelibrary.wiley.com/doi/abs/10.1002/sim.9525). 

### Estimating equations

During my postdoc, Stephen Cole recommended I learn about M-estimation. Since that time, it has changed how I 
approach quantitative research. To me, estimating equations present a set of powerful tools for the conduct of 
epidemiologic research. They have simplified estimation for practical problems, allowed me to design more extensive
simulation studies for novel estimators, and easily develop proofs for asymptotic properties of estimators. Most 
relevant for epidemiologists, they have allowed me to nearly always avoid having to use the bootstrap for variance
estimation. My ongoing interest is in this area is furthering the development of these tools and to ease their 
adoption by epidemiologists. 

My most meaningful contribution in this area (in my opinion) has been the development of 
[delicatessen](https://deli.readthedocs.io/en/latest/), 
a Python library for general application of estimating equations. This has enabled and accelerated my other work in
this area, which includes
[introductory materials](https://pubmed.ncbi.nlm.nih.gov/38423105/) developed for epidemiologists, 
extensions for g-computation with [marginal structural models](https://pubmed.ncbi.nlm.nih.gov/39191643/) or
[time-varying confounding](https://pubmed.ncbi.nlm.nih.gov/39489722/),
use with [sensitivity analyses](https://journals.lww.com/epidem/Abstract/9900/Sensitivity_Analyses_for_Means_or_Proportions_with.139.aspx),
[fusion designs](https://academic.oup.com/aje/article/192/3/467/6564140),
and [bridged treatment comparisons](https://pubmed.ncbi.nlm.nih.gov/38110289/) for comparing across 
randomized trials.

I also conduct workshops on the use of estimating equations. Materials for this workshop are publicly available 
[here](https://github.com/pzivich/ABCs_of_M-estimation).

### Infectious diseases

My applied work focuses mainly on infectious disease epidemiology. Previous and ongoing research have focused on 
[HIV](https://pubmed.ncbi.nlm.nih.gov/37969014/), 
[influenza](https://cdr.lib.unc.edu/concern/dissertations/9p290j79m),
[pneumonia](https://link.springer.com/article/10.1186/s41479-018-0055-4),
[SARS-CoV-2](https://www.researchprotocols.org/2021/4/e25410), 
[testing strategies](https://academic.oup.com/aje/article/192/2/246/6759402),
and 
[vaccines](https://link.springer.com/article/10.1007/s10995-016-2201-z). 


------------------

## External links

- [ORCID](https://orcid.org/0000-0002-9932-1095)
- [GoogleScholar](https://scholar.google.com/citations?user=hbU-gZ0AAAAJ&hl=en)
- [BlueSky](https://bsky.app/profile/pausalz.bsky.social)
- [GitHub](https://github.com/pzivich)
- [ResearchGate](https://www.researchgate.net/profile/Paul-Zivich)
- [CrossValidated](https://stats.stackexchange.com/users/247479/pzivich)
