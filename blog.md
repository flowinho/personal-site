---
layout: page
title: "Blog"
uikit-icon: "rss"
permalink: /blog/
---
<!-- <div class="uk-placeholder">Hier kommt noch was, versprochen. 😏</div>

<span class="uk-text-meta"><a href="/entwickler-blog/">Hier geht es zu allen Posts aus der Kategorie "der Entwickler".</a></span><br /> -->

<div class="" uk-grid>
    <div class="uk-width-1-3@m">
        <h2><span uk-icon="git-branch"></span> der Entwickler</h2>
          <ul class="post-list">
          {%- for post in site.categories["derEntwickler"] -%}
          <li>
            <a href="{{ post.url | relative_url }}"><span uk-icon="file-text"></span> {{ post.title | escape }}</a><br />
            {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
            <span class="post-meta">{{ post.date | date: date_format }}
                    <span class="post-meta post-list-tags">
                      {% if post.tags.size > 0 %}
                      <br />
                      <span uk-icon="tag"></span>&nbsp;{{ post.tags | sort | join: " " }}
                            {% endif %}
                    </span>
              </span>
            {%- if site.show_excerpts -%}
              {{ post.excerpt }}
            {%- endif -%}
          </li>
          {%- endfor -%}
        </ul>
    </div>
     <div class="uk-width-1-3@m">
        <h2><span uk-icon="heart"></span> der Papa</h2>
          <ul class="post-list">
          {%- for post in site.categories["derPapa"] -%}
          <li>
            <a href="{{ post.url | relative_url }}"><span uk-icon="file-text"></span> {{ post.title | escape }}</a><br />
            {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
            <span class="post-meta">{{ post.date | date: date_format }}
                    <span class="post-meta post-list-tags">
                      {% if post.tags.size > 0 %}
                      <br />
                      <span uk-icon="tag"></span>&nbsp;{{ post.tags | sort | join: " " }}
                            {% endif %}
                    </span>
              </span>
            {%- if site.show_excerpts -%}
              {{ post.excerpt }}
            {%- endif -%}
          </li>
          {%- endfor -%}
        </ul>
    </div>
     <div class="uk-width-1-3@m">
        <h2><span uk-icon="comment"></span> der Podcaster</h2>
          <ul class="post-list">
          {%- for post in site.categories["derPodcaster"] -%}
          <li>
            <a href="{{ post.url | relative_url }}"><span uk-icon="file-text"></span> {{ post.title | escape }}</a><br />
            {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
            <span class="post-meta">{{ post.date | date: date_format }}
                    <span class="post-meta post-list-tags">
                      {% if post.tags.size > 0 %}
                      <br />
                      <span uk-icon="tag"></span>&nbsp;{{ post.tags | sort | join: " " }}
                            {% endif %}
                    </span>
              </span>
            {%- if site.show_excerpts -%}
              {{ post.excerpt }}
            {%- endif -%}
          </li>
          {%- endfor -%}
        </ul>
    </div>
</div>