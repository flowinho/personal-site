---
title: "How-to: Darstellung von Tags in Jekyll posts"
layout: post
tags: scss css html liquid
categories: derEntwickler
---


Ah, endlich etwas eye-candy! Als erstes sollten wir, wenn nicht bereits geschehen, eine Kopie des `posts.html` Layouts unserer aktuellen Jekyll Theme anlegen, in dem wir diese aus dem Minima-Ordner nach `_layout/post.md` kopieren.

Jetzt suchen wir uns die Stelle innerhalb des Templates in dem die Tags angezeigt werden sollen.

```html
<header class="post-header">
    <h1 class="post-title p-name" itemprop="name headline">{{ page.title | escape }}</h1>
    <p class="post-meta">
      <time class="dt-published" datetime="{{ page.date | date_to_xmlschema }}" itemprop="datePublished">
        {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        {{ page.date | date: date_format }}
      </time>
      {%- if page.author -%}
        • <span itemprop="author" itemscope itemtype="http://schema.org/Person"><span class="p-author h-card" itemprop="name">{{ page.author }}</span></span>
      {%- endif -%}
      //
      // Vielleicht hier??!
      //
    </p>
  </header>
```

**Schritt 1**: Die Tags sollen nur sichtbar sein, wenn wirklich Tags vergeben. Das ist recht einfach umzusetzen durch einen Zugriff auf die liquid-collection `page.tags`.

```liquid
{% raw %}{% if page.tags.size > 0 %}
  // do something
{% endif %}{% endraw %}
```

**Schritt 2**: Plural -- Wir sollten ein "s" hinzufügen, falls mehr als ein Tag gefunden wurde.


```liquid
{% raw %}Tag{% if page.tags.size > 1 %}s{% endif %}:{% endraw %}
```

**Schritt 3**: Alle Tags mit Hilfe der `filter` Funktionen von Liquid auflisten:

```liquid
{% raw %}{{ page.tags | sort | join: ", " }}{% endraw %}
```

**Alles zusammen:**

```liquid
{% raw %}{% if page.tags.size > 0 %}
  Tag{% if page.tags.size > 1 %}s{% endif %}: {{ page.tags | sort | join: ", " }}
{% endif %}{% endraw%}
```

Das volle Snippet sieht am Ende so aus:

```html
<p class="post-meta">
    <time class="dt-published" datetime="{{ page.date | date_to_xmlschema }}" itemprop="datePublished">
    {% raw %}{%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
    {{ page.date | date: date_format }}
    </time>
    {%- if page.author -%}
    • <span itemprop="author" itemscope itemtype="http://schema.org/Person"><span class="p-author h-card" itemprop="name">{{ page.author }}</span></span>
    {%- endif -%}
    {% if page.tags.size > 0 %}
        - Tag{% if page.tags.size > 1 %}s{% endif %}: {{ page.tags | sort | join: ", " }}
    {% endif %}{% endraw %}
</p>
```