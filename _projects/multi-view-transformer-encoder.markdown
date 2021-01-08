---
layout: page
title: AGWE with Transformer encoders
description: Investigating the performance of Transformer encoders when learning word embeddings from acoustic signal and character string.
img: /assets/img/200531_multiple_embeddings.png
importance: 2
---

# Overview

This is a project my partner [Rujual Bains](https://stat.uchicago.edu/people/profile/rujual-singh-bains/){:target="\_blank"} and I did for our Speech Technologies class with Professor [Karen Livescu](https://ttic.uchicago.edu/~klivescu/){:target="\_blank"} (TTIC 31190). We tried to improve upon the quality of acoustically grounded word embeddings (agwe) obtained from a multi-view setup (acoustic and character) by using Transformer encoders instead of bidirectional LSTMs for each view. These three images can summarize the concept of the project. I will go into more detail about each below.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/200531_multiple_embeddings.png' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/200531_multiview.png' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/200531_multiview_transformer.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    First image: idea of acoustic word embeddings. Second image: the framework which we modified. Third image: our changes to the frame work (replacing BiLSTMs with Transformer encoders.)
</div>


# Acoustic word embeddings

The goal of this project was to try to improve upon acoustically grounded word embeddings, but it is instructive to first know what are *acoustic word embeddings*. Acoustic word embeddings are a finite-dimensional representation of an acoustic signal of arbitrary length; in other wrods, they are a mapping of a sequence of acoustic frames to a vector. This idea can be seen in the photo below. Acoustic word embeddings are a tool gaining traction in automatic speech recognition (ASR), which is the task of recognizing a sequence of words in a language given the acoustic signal (the audio / speech itself), because of the potential increase in simplicity and efficiency they offer when compared to doing ASR with sub-word representations. They also offer interesting prospects for the representation of distance between acoustic signals, which is interesting for spoken term detection tasks. 


<div class="row justify-content-md-center">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/200531_multiple_embeddings.png' | relative_url }}" alt="" title="example image"/>
</div>
<div class="caption">
    An example of two acoustic signals (i.e. sequence of frames; i.e. samples of speech) being mapped to a point (vector) in a three-dimensional space. Typically, we use spaces of dimension much greater than three, but the idea is the same.
</div>


# Acoustically grounded word embeddings (agwe)

## Acoustically grounded word embeddings versus acoustic word embeddings

*Acoustically grounded word embeddings* are embeddings of written words which are based on the acoustic/phonetic content. So, the difference between acoustic word embeddings and acoustically grounded word embeddings is this: acoustic word embeddings are obtained by a function which maps a spoken word to a point in a vector space; acoustically grounded word embeddings are obtained by a function which takes a written word with some acoustic information about that word and maps it to a point in a vector space. The difference is admittedly a bit subtle, but it is important. Acoustic word embeddings are nice but limited: one of the first things you learn in a phonology course is that although we perceive each instance of the *basketball* as more or less the same, the production of this word, even within a single speaker, is incredibly variable, and this variability limits acoustic word embeddings in ASR. Acoustically grounded word embeddings, on the other hand, deal with written language, which is for the most part static, and this stability allows for more flexibility in its application, however paradoxical that may sound.

## Obtaining acoustically grounded word embeddings

There are several ways you can imbue word embeddings with acoustic information. The strategy [Rujual](https://stat.uchicago.edu/people/profile/rujual-singh-bains/){:target="\_blank"} and I used was based on one that our professor [Karen Livescu](https://ttic.uchicago.edu/~klivescu/){:target="\_blank"} and a few of her students, mainly [Shane Settle](https://github.com/shane-settle){:target="\_blank"} and [Wanjia He](https://www.linkedin.com/in/wanjia-he-435004a5){:target="\_blank"}, worked on. A couple of great papers for more background are by [Settle et al.](https://arxiv.org/pdf/1903.12306.pdf){:target="\_blank"} and [He et al.](https://arxiv.org/pdf/1611.04496.pdf){:target="\_blank"}. We had a multi-view setup like the work just referenced: we used information from the sequence of characters in the word itself (as spelling isn't entirely arbitrary when it comes to acoustics) and information from a spoken example of that word (this signal obviously full of acoustic information). The goal was to learn a set of vectors where written words which sounded the same were closer to each other. Distance was measured by cosine similarity (which in our case is the angle between the two vectors). A more detailed version of the second image above, which shows the multi-view framework which we modified, can be found below.


<div class="row justify-content-md-center">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/200531_multiview_setup.png' | relative_url }}" alt="" title="example image"/>
</div>
<div class="caption">
    The multi-view acoustic word embedding framework which we modified.
</div>


# Our modifications

Pretraining (semantic + syntactic) word embeddings with Transformers has gained a lot of popularity in Natural Language Processing (NLP), largely due to the Transformer's efficiency in training and equal-to-better than state-of-the-art performance on many tasks. The learning of acoustically grounded word embeddings is also a pretraining task with a similar desired outcome: we want embeddings which capture meaningful linguistic information. The success of Transformers in NLP had us wonder whether this same success could be seen in speech technologies, like improving acoustically grounded word embeddings. So, [Rujual](https://stat.uchicago.edu/people/profile/rujual-singh-bains/){:target="\_blank"} and I modified the multi-view framework above by substituting the bidirectional LSTMs found in the previous work with Transformer encoders to serve as the embedding (encoding) function for the acoustic signal and sequence of characters. Below, you'll see a simplified representation of what we did as well as a more detailed representation of the component of interest, which is the Transformer encoder.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/200531_multiview_transformer.png' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/transformer5.JPG' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    First image: the modifications we made to the existing framework. Second image: the Transformer encoder itself.
</div>


# Results

We unfortunately didn't improve upon the previous approach (based on average precision), but we did do better than some other approaches. The acoustic view results pertain to just the acoustic word embeddings learned in the multi-view setup, and the cross-view results reference the joint embeddings. Few people have considered the multi-view approach, so that is why there are fewer points of comparison in the second table. Our approach did much better learning acoustic word embeddings than it did acoustically grounded word embeddings.

<div class="row justify-content-lg-center">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210107_multiview-transformer-encoder-results.png' | relative_url }}" alt="" title="example image"/>
</div>
<div class="caption">
    Results from our project.
</div>



# For more information

Please feel free to reach out to me if you have any questions regarding the project! You can check out the code at my [repository](https://github.com/rhodb/agwe_transformer){:target="\_blank"}, and you can check out the paper <a href= "{{ '/assets/pdf/200612_finalreport_multiview_transformer_encoder.pdf' | relative_url }}">here</a>.
