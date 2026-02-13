---
layout: page
title: AI Manifesto
description: Overview of my philosophy
---


[Others](https://www.bydamo.la/p/ai-manifesto) have suggested and made an "/ai manifesto" page on their websites, 
so this is my attempt. It reflects my current thoughts and perspective.

First, I think it is worthwhile to delineate what is meant by 'AI', since this is an 'AI manifesto'. I find the term
'AI' to be an overused and unhelpful term. 'AI' and 'LLM' are conflated to an extent that makes AI fairly meaningless 
as a term for differentiation. If by 'AI', one means machine learning (beyond LLMs), then I would generally say that 
'AI' has some utility. I think various applications (chemical structures, protein structures, etc.) show promise for 
exploratory purposes, but I think there are large gaps remaining. Pursuing those avenues of research is worthwhile. 
In my own work, use of machine learning appears to have some utility for nuisance function estimation (e.g., propensity
scores for inverse probability weighting), but I am a bit more skeptical of how useful it will prove to be than many of 
my peers. I also think when machine learning is used, many of the challenges 
([convergence rates](https://pubmed.ncbi.nlm.nih.gov/33591058/) and 
[random seed dependence](https://pubmed.ncbi.nlm.nih.gov/39150866/)) are not properly 
addressed (partly because they make application of these methods more difficult). 
The remainder of this page focuses on LLMs.

### Large Language Models

My view is that LLMs have some uses, but these are far narrower than what is advertised by businesses financially 
invested in their uptake. I have a general interest in how statistical model operate in different tasks 
(hopefully unsurprising given you made it to this page on my website). I have previous made simple character-based 
text generators, with code publicly available [here](https://github.com/pzivich/RNN-Abstract-Generator). 
When building your own text generator, their fragility 
becomes quite apparent (when messing with the training set of the model I built, it sometimes would just repeat a single 
sentence due to where the optimizer landed). Ultimately, these are probabilistic models giving a highly likely word 
following a sequence of prior words (which I view as differently from how thinking in humans works). The ability of 
current LLMs to recreate text are impressive, but I think it speaks more to the regularity in language (which would 
seem to be necessary feature to enable complex communication) than any particular 'ghost' inside the statistical 
machine. If anything, I think the propensity for people to interact with them as if they are cognizing beings reveals 
a special place language holds in the human mind. 

The areas where I have used LLMs (and thus think they have some utility):
- Rephrasing sentences I have written (I often hate the phrasing suggested, but it can lead me to something I like).
- [Rubber ducking](https://en.wikipedia.org/wiki/Rubber_duck_debugging) code (again the solution is often not 
  directly provided, but the back-and-forth is helpful. The "conversing" aspect helps speed this up for me)
- Synonyms for fields of study (think thesaurus but for concepts instead of words). Think word2vec
- Criticism of initial ideas (as a simple check on topics I've already thought about)
- Language translation (this is not active on my part, but it underlies some online text translation services)

What I do not use LLMs for:
- Writing scientific papers (this is like a third of my job, so if I hated it that much I would find a different occupation)
- Summarizing published research papers or pre-prints (I've tested this feature on my own papers and it is subpar)
- Teaching or creation of teaching materials
- Any image/audio/video generation for presentations or publications (if I see AI generated images in a 
  presentation it does lower my opinion of the speaker)
- Writing software documentation or examples (it is not good for the areas I work in, where text online is sparse). I've
  tried to get LLMs to write vignettes, but they are not good
- Generating social media posts or text on this website. My thoughts are my own, even the bad ones

Finally, I think use of LLMs is ethically fraught, including issues related to lack of attribution, environmental 
damage, misuse by various actors (propaganda, scams, etc.), workers' rights, and others. I minimize my own uses (where 
I think LLMs can be a useful tool) for these reasons.
