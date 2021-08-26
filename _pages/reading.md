---
layout: archive
title: "Reading Lists"
permalink: /reading/
author_profile: true
redirect_from:
  - /list
  
---

> Mathematical reasoning may be regarded rather schematically as the exercise of a combination of two facilities, which we may call intuition and ingenuity. 
> -[Alan M. Turing](https://en.wikiquote.org/wiki/Alan_Turing)

{% include base_path %}


{% for post in site.technical reversed %}
  {% include archive-single.html %}
{% endfor %}
