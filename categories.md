---
layout: default
title: Categories
permalink: /categories/
---

# Categories

{% if site.categories.size > 0 %}
{% assign sorted_categories = site.categories | sort %}
{% for category in sorted_categories %}
{% assign category_name = category[0] %}
{% assign category_slug = category_name | slugify %}
{% assign posts = category[1] %}
<details class="category-dropdown" id="{{ category_slug }}">
  <summary>
    <span>{{ category_name }}</span>
    <span class="taxonomy-count">{{ posts.size }} post{% if posts.size != 1 %}s{% endif %}</span>
  </summary>
  <ul class="post-list">
    {% for post in posts %}
    <li>
      <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
  </ul>
</details>
{% endfor %}
{% else %}
<p>No categories yet.</p>
{% endif %}

<script>
  (function () {
    function openCategoryFromHash() {
      if (!window.location.hash) {
        return;
      }

      var id = decodeURIComponent(window.location.hash.slice(1));
      if (!id) {
        return;
      }

      var category = document.getElementById(id);
      if (!category || category.tagName.toLowerCase() !== "details") {
        return;
      }

      category.open = true;
    }

    if (document.readyState === "loading") {
      document.addEventListener("DOMContentLoaded", openCategoryFromHash);
    } else {
      openCategoryFromHash();
    }

    window.addEventListener("hashchange", openCategoryFromHash);
  })();
</script>