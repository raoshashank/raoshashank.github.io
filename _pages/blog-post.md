---
layout: page
permalink: /blog/
title: blog post
description: technical and non-technical blog posts.
nav: false
nav_order: 3
pagination:
  enabled: true
  collection: posts
  permalink: /page/:num/
  per_page: 10
  sort_reverse: true
---

Add new posts as markdown files in `/_posts/` (for example: `YYYY-MM-DD-post-title.md`), and keep resources for each post in a matching folder under `/assets/` (for example: `/assets/blog/post-title/`).

<div class="news">
  {% assign post_list = paginator.posts | default: site.posts %}
  {% if post_list and post_list.size > 0 %}
    <div class="table-responsive">
      <table class="table table-sm table-borderless">
        {% for post in post_list %}
          <tr>
            <th scope="row" style="width: 20%">{{ post.date | date: '%b %d, %Y' }}</th>
            <td>
              {% if post.redirect == blank %}
                <a class="news-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
              {% elsif post.redirect contains '://' %}
                <a class="news-title" href="{{ post.redirect }}" target="_blank" rel="noopener noreferrer">{{ post.title }}</a>
              {% else %}
                <a class="news-title" href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
              {% endif %}
            </td>
          </tr>
        {% endfor %}
      </table>
    </div>
  {% else %}
    <p>No posts yet.</p>
  {% endif %}
</div>

{% if paginator %}
{% include pagination.liquid %}
{% endif %}
