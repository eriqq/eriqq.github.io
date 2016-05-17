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
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tag_words[item]  }}{% endcapture %}
    <ul class="tag-list">
    <h2 id="{{this_word}}" class="tags-h2" >{{ this_word | capitalize  }}</h2>
    {% for post in site.tags[this_word] %}{% if post.title != null %}

        <span class="tag-posts" style="float: left;">
          <li> <a href="{{ post.url }}">- {{ post.title }}</a></li>

        </span>

    {% endif %}{% endfor %}</ul>
  {% endunless %}{% endfor %}
</div>
