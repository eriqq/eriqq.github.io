---
layout: no-title-page
title: Tags
description: List of articles and posts by tags.
---

<!-- Get the tag name for every tag on the site and set them
to the `site_tags` variable. -->
{% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}

<!-- `tag_words` is a sorted array of the tag names. -->
{% assign tag_words = site_tags | split:',' | sort %}

<!-- Build the Page -->

<!-- List of all tags -->
<!--<div class="">
<h1>All Tags</h1>
{% for item in (0..site.tags.size) %}{% unless forloop.last %}
{% capture this_word %}{{ tag_words[item]  }}{% endcapture %}
<a class="tags-a" href="#{{ this_word | cgi_escape }}">{{ this_word | capitalize  }}</a>
{% endunless %}
{% endfor %}
</div> -->
<!-- Posts by Tag -->

<div style="clear:both" class="tags-content">
<h1 class="site-title" >Tags</h1>
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tag_words[item]  }}{% endcapture %}
    <div class="tag-container" >
    <h2 id="{{this_word}}" class="tags-h2" >{{ this_word | capitalize  }}</h2>
    <ul class="tag-list">
    {% for post in site.tags[this_word] %}{% if post.title != null %}
    <li> <span class="tag-posts" style="float: left;"> <a href="{{ post.url }}">- {{ post.title }}</a> <span>  {{ post.date | date: "%b %-d %Y" }}</span> </span></li>
    {% endif %}{% endfor %}</ul></div>
  {% endunless %}{% endfor %}
</div>
