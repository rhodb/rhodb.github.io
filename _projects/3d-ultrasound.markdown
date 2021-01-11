---
layout: page
title: 4D ultrasound imaging of /l/ and /r/ in American English
description: A study I helped conduct in Steven Lulich's lab of Speech and Hearing Sciences at Indiana University. The work was joint with Kelly Berkson and Ken de Jong in the linguistics department. We looked at production of /l/ and /r/ in American English with time aligned 3D ultrasound.
img: /assets/img/4d1.png
importance: 4
---

## Overview

This is a small page on a big project I worked on for [Steven Lulich](https://sphs.indiana.edu/about/faculty/lulich-steven.html), [Kelly Berkson](https://www.kellyberkson.com/) and [Ken de Jong](https://cl.indiana.edu/~kdejong/), all at Indiana University. I only worked on it for about a year, the year before I took off for graduate school at the University of Chicago. The goal of the project was to investigate /l/ and /r/ articulation in American English, as the variants of these sounds in American English are less common typologically-speaking. To do this, we used three-dimensional ultrasound over time, making the measurements four-dimensional; so, the ultrasound transducer recorded images in three directions -- forward-backward, left-right and top-bottom --- and we aligned these images over the time of the production. The upshot of this was that after some processing, we could have a reconstruction of a person's vocal tract as they produced these sounds, giving us an idea of the variance and differences in the production. The precedent / proof-of-concept set by this project was incredible. If you have the appropriate access, you can find out more [here](https://sphs.indiana.edu/research/publications/2019-acquiring-and-visualing.html). (I think in a parallel universe, I stayed at Indiana University and continued working on this project...)

## Pipeline

### Getting measurements

I was heavily involved in the running of the experiment. There were many parts: first, we had to make an impression of someone's palate (giving us an idea of the space the tongue is operating when we do the ultrasound imaging)... so think dentist / orthodontist, however unpleasant that may be; second, we took this palate impression and digitized it using a three-dimensional scanner. After this, we put a Frankenstein-like contraption on the person's head, securing the ultrasound transducer underneath their chin so that we could get measurements; last, we had them go into a sound proofed room and do many recordings, where we were looking at the production of /l/'s and /r/'s in word-initial and word-final position. We used the frame *I said a [word-of-interest] again*, where the *word-of-interest* would be something like *roll* or *lore*. You can see the contraption below in the left image and then where the ultrasound transducer would go in the second image.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210111_palate.png' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210111_ultrasound-head-contraption.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/4d2.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Left image: example of a palate impression --- just like at the dentist or orthodontist! Middle image: the contraption which held the transducer in place (this is from a Berkeley lab, but ours was the exact same). Right image: where the ultrasound transducer would go and a visualization of the tongue that it would produce.
</div>

### Processing the data

Getting the data was tough logistically-speaking, but everything flowed harmoniously once you got the hang of it; processing the data was easy conceptually-speaking, but practically very tough to do because there was ***so*** much of it. So, another large labor of love for this study that I was deeply involved in was the processing of the data. Unfortunately, at the time, there were not sufficient machine learning methods to automate the processing, so we had to do most of it by hand. Processing the data consisted of taking each image the ultrasound transducer produced, in every dimension, and tracing the tongue contour in this image. In each image, you are seeing only a partial representation of the tongue at a given point in an utterance, but once you stitch all these representations together, you get the full picture! Below you can see the photo on the left which one would fawn over in the processing phase, as it is perfectly clear where the tongue is; then, on the right, you can see another photo, which is more realistic picture of what the processing phase looks like --- a computer screen with images of the tongue at a point in time in every dimension with the audio and current reconstruction of the tongue available to help you.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210111_ultrasound-tongue.png' | relative_url }}" alt="" title="example image"/>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210111_ultrasound-processing.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Left image: ideal image of a mid-sagittal section of the tongue, where the black dots trace the surface of the tongue. Right image: the more realistic scenario --- acoustic information on the left, (mid-)sagittal slice in the middle on top, anterior slice in the middle on bottom, (partial) reconstruction of the tongue on the top right, superior slice on the bottom right.
</div>


### Upshot

Once we processed all this data, we were able to get reconstructions of the tongue, through time, producing the different articulations. I don't have the videos at the moment, but I will try to get them soon to post here. For now, you can see the picture below! 

<div class="row justify-content-md-center">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/4d1.png' | relative_url }}" alt="" title="example image"/>
</div>
<div class="caption">
    The tongue configuration for /r/ in the production of the words *lore* and *rock* for a speaker from New Hampshire. The yellow dots are the palate, and the lines are contours of the tongue, with red indicating the middle and green the periphery. The images on the left are visualizing the production as if you are looking at the side of someone's face, specifically their left side. The images on the right would be from the perspective of looking down on the person on the left. You can see this interesting bunching, causing a cavity in the body of the tongue!
</div>


## More information

I helped present this work as a poster at the 2015 Meeting of the Journal of the American Acoustical Society with [Steven Lulich](https://sphs.indiana.edu/about/faculty/lulich-steven.html), [Kelly Berkson](https://www.kellyberkson.com/) and [Ken de Jong](https://cl.indiana.edu/~kdejong/). It was a really fun trip, and people were very excited about the work. After presenting this work, my main task was documenting the protocols for the experiment, and once I did that, it was basically time for me to leave to graduate school, and I haven't worked on the project since. The poster had a <a href= "{{ '/assets/pdf/leftpanelASAposter.pdf' | relative_url }}">left</a>, <a href= "{{ '/assets/pdf/centerpanelASAposter.pdf' | relative_url }}">center</a> and <a href= "{{ '/assets/pdf/rightpanelASAposter.pdf' | relative_url }}">right</a> panel, so please feel free to check it out! We also hung an iPad with the videos, which people seemed to love. Again, you may need appropriate access, but please do check out their [paper](https://sphs.indiana.edu/research/publications/2019-acquiring-and-visualing.html) on this work as well.