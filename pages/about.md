---
layout: page
title: About
permalink: /about/
weight: 1
---

{% include about/about.html %}

<div class="row">
{% include about/skills.html title="ML/AI Skills" source=site.data.ml-skills %}
{% include about/skills.html title="LLM Skills" source=site.data.llm-skills %}
{% include about/skills.html title="Full Stack Skills" source=site.data.fullstack-skills %}
</div>

<div class="row">
{% include about/timeline.html %}
</div>