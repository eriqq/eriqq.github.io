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
<div class="post__showtags" >
<h2 class="tag-list" >Tag List</h2>
<ul class="post__tags">
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tag_words[item] }}{% endcapture %}
    <li>
      <a href="#{{ this_word | cgi_escape }}" class="tag">{{ this_word | capitalize }}
        <span>({{ site.tags[this_word].size }})</span>
      </a>
    </li>
  {% endunless %}{% endfor %}
</ul>
</div>
<!-- Posts by Tag -->
<div style="clear:both" class="tags-content">
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tag_words[item]  }}{% endcapture %}
    <h2 class="tags-h2" id="{{ this_word | cgi_escape }}">{{ this_word | capitalize  }}</h2>
    {% for post in site.tags[this_word] %}{% if post.title != null %}
      <div>
        <span class="tag-posts" style="float: left;">
          <a href="{{ post.url }}">{{ post.title }}</a>
        </span>
        <span style="float: right;">
          {{ post.date | date_to_string }}
        </span>
      </div>
      <div style="clear: both;"></div>
    {% endif %}{% endfor %}
  {% endunless %}{% endfor %}
</div>
