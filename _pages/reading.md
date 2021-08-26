---
layout: archive
title: "Reading Lists"
permalink: /reading/
author_profile: true
redirect_from:
  - /list
  
---

> Programming is one of the most difficult branches of applied mathematics; the poorer mathematicians had better remain pure mathematicians.
> -[Edsger W. Dijkstra](https://en.wikiquote.org/wiki/Edsger_W._Dijkstra)

{% include base_path %}


{% for post in site.reading reversed %}
  {% include archive-single.html %}
{% endfor %}
