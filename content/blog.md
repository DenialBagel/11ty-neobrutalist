---
title: Blog
description: Update from my blog post
pagination:
  data: collections.posts
  size: 5
  reverse: true
testdata:
 - item1
 - item2
 - item3
 - item4
permalink: "blog/{% if pagination.pageNumber > 0 %}page-{{ pagination.pageNumber + 1 }}/{% endif %}index.html"
---
<section class="alert info">
<h2><a href="{{page.url}}" class="non">{{title}}</a></h2>
<h3>{{description}}</h3>
<div class="grid-container">
{%- for post in pagination.items %}
<div class="grid-item">
<div class="card  alert warning">
<a href="{{post.url}}">
<div class="card-thumbnail">
<img src="{{post.data.image or metadata.image}}" loading="lazy" alt="{{post.data.title or metadata.title}}" class="card-thumbnail"/>
</div>
<div class="card-content">
<div class="text-small"><time datetime="{{ post.date | htmlDateString }}">{{ post.date | readableDate("dd LLLL yyyy") }}</time></div>
<h3><strong>{{post.data.title}}</strong></h3>
<!--<p>{{post.data.description}}</p>-->
</div>
</a>
</div>
</div>
{% endfor %}
</div>
<div class="alert warning">
<div class="marquee-content">
{% if pagination.href.previous %}<a href="{{ pagination.href.previous }}" class="nb-button default" aria-label="Previous Blog List Article">← Previous</a>{% endif %}
{% if pagination.href.next %}<a href="{{ pagination.href.next }}" class="nb-button default" aria-label="Next Blog List Article">Next →</a>{% endif %}
</div>
</div>
</section>
