---
layout: archive
title: "Sitemap"
permalink: /sitemap/
author_profile: true
---

{% include base_path %}

This sitemap lists the main public sections of the site. An [XML version]({{ base_path }}/sitemap.xml) is also available.

<h2>Pages</h2>
<ul>
  <li><a href="{{ base_path }}/">Home</a></li>
  {% for link in site.data.navigation.main %}
    {% if link.url contains 'http' %}
      {% assign domain = '' %}
    {% else %}
      {% assign domain = base_path %}
    {% endif %}
    <li>
      <a href="{{ domain }}{{ link.url }}">{{ link.title }}</a>
      {% if link.children %}
        <ul>
          {% for child in link.children %}
            {% if child.url contains 'http' %}
              {% assign child_domain = '' %}
            {% else %}
              {% assign child_domain = base_path %}
            {% endif %}
            <li><a href="{{ child_domain }}{{ child.url }}">{{ child.title }}</a></li>
          {% endfor %}
        </ul>
      {% endif %}
    </li>
  {% endfor %}
</ul>
