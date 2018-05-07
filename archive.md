---
layout: page
title: Archive
description: 
permalink: archive
sitemap:
    priority: 1.0
    lastmod: 2017-11-02
    changefreq: weekly
---

<h1>Archive</h1>

{% capture site_tags %}
{% for tag in site.tags %}
{{ tag | first }}{% unless forloop.last %},{% endunless %}
{% endfor %}
{% endcapture %}

{% assign tags_list = site_tags | split:',' | sort %}

{% for item in (0..site.tags.size) %}{% unless forloop.last %}
  {% capture this_tag %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
  <article>

  <div class="tag-title" id="{{ this_tag }}">
    <h2> {{ this_tag }} </h2>
  </div>
    <ul>
    {% for post in site.tags[this_tag] %}
    {% if post.title != null %}
      <li class="tag-post">
        {% if post.link %}
        <a href="{{ post.link }}">
        {% else %}
        <a href="{{ post.url | prepend: site.baseurl }}">
        {% endif %}  
          <span class="tag-post-title">{{ post.title }}</span>
        </a>
      </li>
    {% endif %}
    {% endfor %}
    </ul>
  </article>
{% endunless %}
{% endfor %}