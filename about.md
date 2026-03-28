---
layout: default
title: About
permalink: /about/
---

# About

I'm Jared.

This site is where I publish posts about things I'm thinking through, learning, or building.

If you've found something useful here, that's the point.

## Social

<ul>
	{% for link in site.author.links %}
	<li><a href="{{ link.url | relative_url }}">{{ link.title | downcase}}</a></li>
	{% endfor %}
</ul>
