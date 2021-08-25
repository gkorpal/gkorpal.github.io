---
layout: archive
title: "Scholarly Articles"
permalink: /scholarly/
author_profile: true
---
>A very great deal more truth can become known than can be proven.
> -[Richard Feynman](https://en.wikiquote.org/wiki/Richard_Feynman)


{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
