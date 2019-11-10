---
layout: page
title: About
permalink: /about/
weight: 5
---

# **About Me**

Hi I am **{{ site.author.name }}**,<br>
and I am currently a Master Student in Physics at ETH Zürich in Switzerland.

<div class="row">
{% include about/skills.html title="Programming Skills" source=site.data.programming-skills %}
{% include about/skills.html title="Other Skills" source=site.data.other-skills %}
</div>

## Education

<div class="row">
{% include about/timeline.html %}
</div>
