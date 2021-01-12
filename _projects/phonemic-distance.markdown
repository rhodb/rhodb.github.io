---
layout: page
title: Phonemic distance in dialects of Arabic
description: I worked on a phonemically-based way to compute the distance between two dialects of Arabic. This was work for my second qualifying paper for the PhD program at the University of Chicago.
img: /assets/img/210111_dialect-factor.png
importance: 5
---

## Overview

This was the work done for my second qualifying paper for the PhD program in linguistics at the University of Chicago; the readers were [John Goldsmith](http://people.cs.uchicago.edu/~jagoldsm/) and [Jason Riggle](https://linguistics.uchicago.edu/jason-riggle). This was really the first time I waded out into the deep end of independent research with really no one but myself to direct what I was doing; luckily, [John](http://people.cs.uchicago.edu/~jagoldsm/) and [Jason](https://linguistics.uchicago.edu/jason-riggle) afforded me the precious opportunity to do this and grow (not all graduate students are as fortunate to do this). The idea behind this work was to try to get a sense of the distance between two dialects of Arabic. Arabic is interesting because it has *many* dialects, but all of them are close enough to be comparable; moreover, Arabic has an established standard dialect as well, known as Modern Standard Arabic (MSA). It's the coupling of these two facts which facilitates the comparison of dialects: in other words, comparing dialects becomes much easier when you have a reference point you can fix for those comparisons! In a way, you can think about it in terms of Pythagorean's Theorem: if you know the distance of one dialect from the standard variety and you know the distance of another dialect from the standard, then you also can compute the distance between the dialects.

## Inspiration / launching point for this work

I became inspired to do this project for a couple of reasons: (i) I love the Arabic language; and (ii) there was an amazing [paper](https://www.mitpressjournals.org/doi/full/10.1162/COLI_a_00169?mobileUi=0) by [Zaidan](https://scholar.google.com/citations?user=bahbb80AAAAJ&hl=en) and [Callison-Burch](https://www.cis.upenn.edu/~ccb/) pertaining to Arabic dialect identification. In the paper, the authors were concerned with the classification task of identifying dialects of Arabic, where they focused on the whole-word, or morpheme level (by morpheme, you can think in plain English as words). Although they included the plot you see below in their paper, they did not pursue dialect identification at the phonemic level (by phoneme, you can think in plain English as speech sounds). I wanted to extend their work by looking at differences between dialects at a phonemic level, and then I eventually ended up taking the project in a less practically-oriented direction. My goal became not to perform a classification task well but to better understand the differences between the dialects.

<div class="row justify-content-md-center">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210111_dialect-factor.png' | relative_url }}" alt="" title="example image"/>
</div>
<div class="caption">
    The plot from the Zaidan and Callison-Burch paper which inspired me. They plot the various characters in the Arabic alphabet against what they call 'dialectness factor' and frequency. Characters closer to the center as less dialectal and ones towards the periphery are more dialectal. You can see a general triangular shape in these plots, which aligns well with observations in linguistic research, showing that more frequent linguistic objects tend to be less dialectal and more standardized.
</div>


## *Dialectness factor*

I was fortunate enough to get my hands on the [PADIC corpus (A Parallel Arabic DIalect Corpus)](https://www.aclweb.org/anthology/Y15-1004.pdf); this was amazing because it was translated ***phonemically*** in parallel.[^1] This corpus contained translations for two dialects in Algeria, the Algiers and Annaba dialect, and then the general dialects of Morocco, Palestine and Syria as well as Modern Standard Arabic (MSA). To get a sense for what phonemes were 'dialectal' and which were not, I compared how frequently one phoneme occured in a dialect versus how much it occurred in the standard, MSA. I did this by taking ratios, but I won't go into the details here --- please see the <a href= "{{ '/assets/pdf/180506_qpfinal_RhodesBrandon.pdf' | relative_url }}">paper</a> itself for those details. So, I was able to reproduce that plot you see above from [Zaidan](https://scholar.google.com/citations?user=bahbb80AAAAJ&hl=en) and [Callison-Burch](https://www.cis.upenn.edu/~ccb/) for each one of the dialects. I'll just show the ones for the Palestinian (left) and Syrian (right) dialects.


[^1]: The link above unfortunately doesn't go straight to the corpus... this was a few years ago that I did the project and I wasn't able to find the site with the corpus on a quick search. I'll find it eventually.) 


<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210111_dialect-factor-palestinian.png' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210111_dialect-factor-syrian.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Left image: *dialectness factor* for Palestinian dialect. Right image: *dialectness factor* for Syrian dialect. How to read this plot: think of the black line as being the standard; anything phoneme that falls to its left means it occurs less in the dialect than in the standard and any phoneme which falls to the right means it occurs more in the dialect than the standard. You can see that the 'sh' phoneme (which is $ in this plot, and ش in the Arabic script) is pretty positively dialectal for both dialects. For the Syrian dialect, you also see [b] is positively dialectal, which is an encouraging find as present tense verbs in that dialect are conjugated with a [b] (which is more technically an aspectual marker if I remember correctly).
</div>


## Visualizing and comparing the *dialectness factor*

Once you compute the *dialectness factor* for each phoneme in each dialect, you can start to make comparisons, along many directions. First, you can look at comparisons for a single phoneme between different dialects, as you seen below. Any bar that extends above zero means the phoneme occurs more in a dialect, and if a bar extends below zero, it means that phoneme occurs less in the dialect (when compared to the standard, MSA). There are many more plots, but I'll just provide a couple of plots, one for the sounds غ (left) and ق (right), which are similar to the French [r] sound and a hard [k] sound.[^2] These plots give us an idea of how each dialect is behaving.


[^2]: These are a pharyngeal fricative and uvular stop respectively.


<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210111_dialect-loadings-g.png' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210111_dialect-loadings-q.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Left image: plot of the *dialectness factor* for the sound corresponding to غ in the Arabic alphabet, which is similar to the French [r]. Right image: plot of the *dialectness factor* for the sound corresponding to ق in the Arabic alphabet, which is similar to a 'hard' [k] sound --- i.e. just produce a [k] further back in your mouth! We see that the French [r] sound is much more dialect for Moroccans, as is in line with the well-documented history they have with the French. We see that the uvular stop is much less common in the Syrian dialect, which is also interesting, as folks in the Arabic world sometimes make fun of that dialect for not having that 'strong' sound.
</div>


You can also look at the dialectness factors of classes of sounds which are similar to each other and then compare the dialects based on these class distances. Or, you can visualize where each of these dialects fall in some mathematical space, where each dimension corresponds to a phoneme! You can see these below. There is much more in my <a href= "{{ '/assets/pdf/180506_qpfinal_RhodesBrandon.pdf' | relative_url }}">paper</a>.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210111_dialect-stop-distances.png' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210111_dialect-embeddings.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Left image: table showing the distances between the dialects for stops (so, consonants like b, t, d, k...). Right image: a plot showing the configuration of dialects with respect to a few consonants. For the right image, think of the origin as being the standard, MSA, and the position of each dialect as how far they vary from that standard (and hence each other!). We see that the dialects located in Africa (Annaba, Algiers and Morocco) are clustered together in this space while the ones in Western Asia (Palestine, Syria) are apart from that cluster and closer to one another. 
</div>


## Upshort

At the end of this work, I basically developed a notion of phonemic distance, which was pretty interesting. This can be extended to more general situations, but it is tricky because my work depended on there being a standard, a point which we fix so that we can make comparisons. There is not really a clear point like this when you are doing comparisons between different languages. However, this project changed pretty profoundly my philosophy on what actually is a dialect and what actually is a language. The body of linguistic information for a given language or dialect can be mapped to a point in some high-dimensional linguistic space, and what we usually refer to as a 'language' is really just a limiting point in this space (borrowing language from topology, if I may), determined by cultural-historical forces, and dialects are just points within the a certain sized neighborhood of this limiting point. 


## Closing thoughts and more information

This is probably the most interesting work I think I've done, though, it was earlier in my development, so if I were to work on it again, I would approach it in a much more sophisticated way. :) Please do take a look at my actual <a href= "{{ '/assets/pdf/180506_qpfinal_RhodesBrandon.pdf' | relative_url }}">paper</a> if you are interested.
