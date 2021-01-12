---
layout: page
title: Stress and syllabification with Dynamic Computational Networks
description: I investigated the possibilities and properties of Dynamic Computational Networks when jointly accounting for stress and syllabification (in English).
img: /assets/img/210112_dcn-jointmodeling.png
importance: 4
---

190609_proposal-final

190609_presentation

## Overview

For my dissertation proposal at the University of Chicago, I worked on extending work done by [Goldsmith](http://people.cs.uchicago.edu/~jagoldsm/) and Larson in the 1990s on a neural network architecture they called a Dynamic Computational Network (DCN). This was a bunch of fun, as [John](http://people.cs.uchicago.edu/~jagoldsm/) was happy to be thinking about this problem again, and it was a way for me to think about how I could relate modern statistical and machine learning methods into a classical problem in linguistics and an previous, and promising, framework for that problem, DCNs. I haven't done much work since, as I've gone off in different directions for the dissertation, but this has always been in the back of my mind, waiting to be revisited. I believe this theory should really be developed, as it is a simple, yet very powerful, framework which does seem to actually set theory on a track towards neurological plausibility --- something I feel should be thought about more. This project page will definitely not cover everything in the proposal itself, but please feel free to look at the actual <a href= "{{ '/assets/pdf/190609_proposal-final.pdf' | relative_url }}">proposal</a> and <a href= "{{ '/assets/pdf/190609_presentation.pdf' | relative_url }}">presentation</a> I gave during my defense of it, which should help clarify points of uncertainty. [Jason Riggle](https://linguistics.uchicago.edu/jason-riggle) is the chair, and [John Goldsmith](190609_presentation) and [Diane Brentari](https://signlanguagelab.uchicago.edu/) are members on my dissertation committee. 


## Preliminaries and motivation

* Stress: think about stress in English as where the emphasis of a word goes: *CONduct* = noun, *conDUCT* = verb

* Syllabification: the syllable structure in a word: *about* is pronounced as *a-bout* and not *ab-out*, so the syllable structure has *a* and *bout* separated as *a.bout* and not *ab* and *out* separated as *ab.out*.


As with many linguistic phenomena, children are typically not taught this explicitly for the majority of the words they know in their language --- *they just learn it*. So, one of the jobs of the linguist is to uncover the structure in linguistic data, as there must be patterns / structure children exploit to learn language so quickly. Working on the problems of stress and syllabification is interesting because of the similar pattern in them, which I won't elaborate much on because it gets to be a bit technical. For syllabification, there is an alternating wave of sonority, so think soft sound followed by loud sound followed by soft sound; for stress, there is an alternating wave of stress, so think stressed followed by unstressed followed by (secondary) stress. That explanation is admittedly a massive gloss over of these problems, but it is meant to give the reader who has little linguistic experience some type of context; it is not intended for a professional linguist.

## Main ideas

These networks are essentially a kind of recurrent neural network (RNN); or, DCNs at least most closely resemble RNNs. DCNs differ in a couple of salient ways, though. First, DCNs take a single input embedding for the whole sequence of computations, unlike in (most, if not all) RNNs where at each time step *t* there is the output from *t-1* (obtained from computations on the input from time step *t-1*) and new input at step *t*. So, in RNN-talk we can think of DCNs as using one input embedding, which is a sequence of linguistically significant values, and then using ***just*** the hidden state at each subsequent time step for every calculation. Second, computations persist until an equilibrium is reached, which may not happen if the weights are not constrained in the proper way. The second difference is perhaps analogous to the exploding gradient problem in deep learning. Work I did extended these models by adding another layer at each time step. I did this because Goldsmith and Larson's previous work looked at syllabification ***or*** stress (accent) in a language, and I was looking at syllabification ***and*** stress in American English, as I wanted to work on the problem of quantity-sensitive stress systems. Below you will see two photos: the top shows the previous set up, the one found in [Goldsmith](http://people.cs.uchicago.edu/~jagoldsm/) and Larson's works; the second is an instantiation of the general extension to their framework that I proposed.

<div class="row justify-content-md-center">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210112_dcn-onelayer.png' | relative_url }}" alt="" title="example image"/>
</div>
<div class="caption">
    The original architecture in Goldsmith and Larson's works.
</div>

<div class="row justify-content-md-center">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210112_dcn-twolayer.png' | relative_url }}" alt="" title="example image"/>
</div>
<div class="caption">
    An instance of the general extension I proposed to their work. We see to account for syllabification and accent and their interactions, we can introduce another layer with connections to the other layer.
</div>


Above in the bottom picture, you see an instantiation of the general extension; below, you can see the general extension itself. The idea is that to account for syllabification and accent jointly, we can introduce another layer and posit various connections between the layers. Each connection and node configuration (i.e. each different architecture) expresses a different way of passing or sharing information. Presumably, different languages will vary by their architecture or settings for the parameters of the architecture, which are denoted by the Greek letters in the diagrams. These parameters basically determine how much information is passed along that connection, affecting the outcome of that information flow. I name the layers as accent and syllabification layers because they correspond to the same (hierarchical) structure which is found in much of the more traditional work on the topic. Typically, we interpret each node in the syllabification layer corresponds to a phoneme and each node on the accent layer corresponds to a syllable; so, under this interpretation, the number of nodes in the accent layer is constrained to be no greater than the number of nodes in the syllabification layer.


<div class="row justify-content-lg-center">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210112_dcn-jointmodeling.png' | relative_url }}" alt="" title="example image"/>
</div>
<div class="caption">
    The general extension that I proposed. Connections can be uni- or bi-directional; they can exist or not exist; the two layers can have an equal amount of nodes or different (but linguistically it makes most sense for the accent layer to have fewer nodes, as accent is thought of as a property of syllables and not phonemic units).
</div>


## Learning the parameters (a bit technical, but I won't go into much detail)

One of the interesting parts of working on DCNs is how they are learned. As I said earlier, for each language, there will be a different setting of the parameters, and one question linguists are interested in is how these parameters (or components of one's language) are learned. Unlike many things in modern machine learning, they are not learned via (stochastic) gradient descent, as there is not a fixed set of computations; computations persist until a certain threshold is reached, and at that point they stop.[^1] What I did, following [Goldsmith](http://people.cs.uchicago.edu/~jagoldsm/) and Larson, was pursue a simulated annealing algorithm. The idea here is that you take a random walk that is constrained in some way --- almost similar to Metropolis-Hastings, if you are familiar with that! I won't talk much about this, but I modified this part to account for the additional layer in the architecture. The extension I think was pretty straightforward, but there are some technical details to work out. Please see the <a href= "{{ '/assets/pdf/190609_proposal-final.pdf' | relative_url }}">proposal</a> and/or <a href= "{{ '/assets/pdf/190609_presentation.pdf' | relative_url }}">presentation</a> for the details.

[^1]: Though now that I think of it, I think you could probably do gradient descent...


## Results

As I explained earlier, the computation happens with just one input, so we can compare the original input (inherent) with the final input (derived). The idea is that the linguistic system (the DCN in our case) works to find the best syllabification structure and best stress structure jointly for any given word. If our model is on the right track, this derived output will be similar to what we observe in reality. The example you see here is for the word *relegate*, which is has stress *RElegate* and syllabification *re.le.gate*.

<div class="row justify-content-lg-center">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210112_dcn-relegate.png' | relative_url }}" alt="" title="example image"/>
</div>
<div class="caption">
    The sonority and accent wave for the word 'relegate'. The inherent sonority wave is in blue and the derived wave (which determines syllabification) is in red; the inherent accent wave is in green and the derived wave (which determines stress) is in yellow. We see the network correctly derives three syllables (three peaks in the red wave), and it correctly places the primary stress on the second syllable, whose nucleus is the vowel in the second position. You can argue the derived accent wave isn't sufficient, thouugh, as there is presumably secondary stress on the last syllable, which doesn't have a peak in that yellow wave. 
</div>


## For more information

Please please please see the <a href= "{{ '/assets/pdf/190609_proposal-final.pdf' | relative_url }}">proposal</a> and/or <a href= "{{ '/assets/pdf/190609_presentation.pdf' | relative_url }}">presentation</a> I did for more details if you are interested. These project pages are not intended to be in-depth explanations of each work, but rather aimed at giving a general impression for the somewhat interested reader. The more interested reader will (hopefully) be much more satisfied after consulting the actual write-ups. The code for this project will make it into a repository at some point, but I need to do some reorganizing of it first.