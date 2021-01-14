---
layout: page
permalink: /publications/
title: Publications
description: Publications I have been a part of over the years.
years: [2018, 2016, 2015, 2014, 2013]
nav: true
---

<div class="publications">

{% for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
