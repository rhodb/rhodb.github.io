---
layout: page
title: Rhythm in speech
description: I wrote some code to get the amplitude envelope of utterances.
github: https://github.com/rhodb/rhythm
importance: 6
---

# Brief description

This project will develop into more over time, but it is starting as just a small codebase for extracting amplitude envelopes for a speech utterance. You can think of the amplitude envelope as the tracing of the overarching structure of an acoustic signal. You can see this below in the images. The images in the second row are the envelopes. 

<div class="row justify-content-md-center">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/210107_amplitude-envelopes.png' | relative_url }}" alt="" title="example image"/>
</div>
<div class="caption">
    Images in the second row are the amplitude envelopes. Photo is taken from [here](https://www.audiolabs-erlangen.de/resources/MIR/FMP/C1/C1S3_Timbre.html){:target="\_blank"}. 
</div>

The exact tracing of the upper amplitude envelope is presumably too rough for the study of rhythm, so in my code there is a parameter to smooth it out so that it captures less detail but more broad structure. Spoiler: as it turns out, I found a much easier / efficient way to do this using Praat, so I don't use this code much anymore. I'll try to clean up and post the code with the Praat script.

# Where to find this code

You can find this code in my repository for it [here](https://github.com/rhodb/rhythm){:target="\_blank"}. 
