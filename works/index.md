---
layout: archive
title: "ShihYao's Works"
date: 2014-05-30T11:39:03-04:00
modified:
excerpt: "A collection of thoughts, inspiration, mistakes, and other minutia."
image:
  feature:
  teaser:
---

{% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
{% assign tags_list = site_tags | split:',' | sort %}

<ul class="entry-meta inline-list">
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
  	<li><a href="#{{ this_word }}" class="tag"><span class="term">{{ this_word }}</span> <span class="count">{{ site.tags[this_word].size }}</span></a></li>
  {% endunless %}{% endfor %}
</ul>

{% for item in (0..site.tags.size) %}{% unless forloop.last %}
  {% capture this_word %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
  <article>
      <h2 id="{{ this_word }}" class="tag-heading">{{ this_word }}</h2>
      <div class="tiles">
        {% for post in site.tags[this_word] %}
          {% include post-grid.html %}
        {% endfor %}
      </div><!-- /.tiles -->
  </article><!-- /.hentry --><br/>
{% endunless %}{% endfor %}
