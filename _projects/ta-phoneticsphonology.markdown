---
layout: page
title: Teaching assistant for Introduction to Phonetics and Phonology
description: A page with materials I developed for the course Introduction to Phonetics and Phonology (LING 20101) at the University of Chicago.
img: /assets/img/210110_ling20101-diphthongs.png
github: https://github.com/rhodb/ling20101-midterm
importance: 9
---

## Overview of the class

I liked being a teaching assistant for this course because it covers material I am more interested in, and it is the first time that the students face serious challenges in learning how to (i) extract linguistic patterns from data and (ii) abstract away principles from these patterns. My goal was still to inspire students, and I found it even more important to make the information digestible for them in this class, as some of the principles in phonology are paramount to understanding contemporary linguistics in general. This class was also interesting in that it is a mix of detailed reality (acoustic phonetics, articulatory phonetics) and abstraction (phonology) away from this reality, so it was fun to try to bridge and motivate that transition, which was new for most students. A part I was heavily involved in was the midterm, which was a phonetics project on their own dialect. I will talk about this more below.


## Materials

I was responsible for leading a discussion each week that was one hour in length. There were forty-four students and only me, so I found it a bit hard to figure out exactly what I should focus on each week, so there was such variance in the group. As with Introduction to Linguistics, I often lectured / reviewed for half of the period and then had an activity or fielded questions the second half. There are lecture materials sitting in the same notebook mentioned on the [page](https://rhodb.github.io/projects/ta-intro) for when I was a teaching assistant for Introduction to Linguistics, and I will at some point get around to making slides or digitizing those notes.

* <a href= "{{ '/assets/pdf/LING20101/181004_discussion1.pdf' | relative_url }}">Introduction to IPA and acoustics</a>
* <a href= "{{ '/assets/pdf/LING20101/181012_discussion2-selected.pdf' | relative_url }}">IPA and preparation for IPA quiz</a>
* <a href= "{{ '/assets/pdf/LING20101/181025_discussion4-1.pdf' | relative_url }}">Midterm help</a>
* <a href= "{{ '/assets/pdf/LING20101/181026_discussion4-2.pdf' | relative_url }}">Phonology</a>
* <a href= "{{ '/assets/pdf/LING20101/181115_portugese.pdf' | relative_url }}">Portuguese</a>


## Midterm project

A major part of this course was the midterm project. For this project, students were asked to write a report on their dialect, using acoustic measurements. This was intentionally open-ended, pushing the students to really think deeper about phonetics (and even think about phonology in a lighter way); as expected, the students had some troubles. Typically, students are much more comfortable with being told exactly what to do, and in this situation they didn't have that structure. At the time I wasn't far removed from being an undergrad as well, so I was a bit sympathetic to their discomfort. To try to help them out, I set up a basic pipeline for them to follow to get measurements, make observations and do basic analysis of their dialect. I'll briefly describe it now, with pointers to the materials.

I first created a set of stimuli for them to get vowel and stop consonant measurements. It was a <a href= "{{ '/assets/pdf/LING20101/181019_stimuli.pdf' | relative_url }}">slide show</a> which consisted of the the frame *I said a [word-of-interest]*, which served to elicit running pronunication of the words-of-interest. (I only told them to focus on the word-initial consonants; otherwise, I would have suggested the frame *I said a [word-of-interest] again*.)

<div class="row justify-content-md-center">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210110_ling20101-diphthongs.png' | relative_url }}" alt="" title="example image"/>
</div>
<div class="caption">
    An example plot showing the diphthongs for the students in the class along with the average trajectory. I love the colors!
</div>

Then, with these repeated measurements I gave them the framework for, I found a Praat script which automatically extracts formant information from an annotated file, and I provided them with <a href= "{{ '/assets/pdf/LING20101/181025_discussion4-1.pdf' | relative_url }}">instructions</a> on how to use it. You can find the script [here](http://www.helsinki.fi/~lennes/praat-scripts/). It turned out to be a little more difficult than I anticipated for the students to run the script, but if I remember correctly, the majority of the students ended up using it and reaping the benefits. You can also find the script in my [repository](https://github.com/rhodb/ling20101-midterm) for this project: it is called `vowelextract`.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210110_ling20101-book.png' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210110_ling20101-monophthong.png' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210110_ling20101-northerncities.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Images representing the process. Left-most image: an example slide from the set of stimuli I made for the students. Middle image: monophthong vowels for class. Right-most image: measurements for the vowel AE (in ARPAbet), the vowel in *bat*, where the contrast is by whether or not the students are from a place in the 'Northern Cities' region (Chicago, Detroit, ...), which is famous in linguistics for the vowel shift which has occurred in their dialect. There doesn't appear to be that much of a difference for the students in the class.
</div>


Last, I used an amazing package in R (`phonR`) to produce a ton of (beautiful, in some cases) plots for the students to use. I registered basic demographic information on the students, and I also provided each of them with a set of plots showing where their vowels and consonant measurements were with respect to the class' measurements and averages. You can see an example of some of those plots above, and you can see a bunch more in the file <a href= "{{ '/assets/pdf/LING20101/181030_data.pdf' | relative_url }}">here</a>.  


## Where to find more plots and some data

You can find more plots and a bunch of data at my repository for the midterm [here](https://github.com/rhodb/ling20101-midterm). The code for the data is not included because it involved using some non-anonymized data, as I used it to produced individual plots for my students to help them out. At some later point, I should edit the code so that it is independent of the identity of the students, and I will then put that in the repository, too.



