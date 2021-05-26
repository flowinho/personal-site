---
title: "How-to: Alle Blogposts mit einem bestimmten Schlagwort auflisten"
layout: post
tags: .html .liquid
categories: derEntwickler
---

Diese Aufgabe lässt sich in Liquid mit Hilfe von ein paar Schleifen und if-else-statements lösen.

1. Falls die Seite posts beinhaltet
2. durchlaufe alle Posts
3. falls ein Post Schlagworte beinhaltet
4. durch alle Schlagworte dieses Posts
5. wenn auf eines der Schlagwörter zB. `.swift` zutrifft
6. stelle ein HTML mit Liquid dar.

```liquid
{% raw %}{%- for post in site.posts -%}
    {%- if post.tags.size > 0 -%}
        {%- for tag in post.tags -%}
            {%- if tag == ".swift" -%}
                // Render HTML
            {% endif %}
        {%- endfor -%}
    {%- endif -%}
{%- endfor -%}{% endraw %}
```
