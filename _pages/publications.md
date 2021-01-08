---
layout: page
permalink: /publications/
title: Publications
description: Publications I have been a part of over the years.
years: [2013, 2014, 2015, 2016, 2018]
nav: true
---

<div class="publications">

{% for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
