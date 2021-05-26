---
title: "Lazy Loading für Bilder zu einem Jekyll blog hinzufügen"
layout: post
tags: .html .js
categories: derEntwickler
---

Es folgt ein 5.44 MB grosses Bild.

![](/assets/posts/2021-03-20-%20david-troeger-9XzyEzPAHMI-unsplash.jpg){:class="lazyload"}

Photo by <a href="https://unsplash.com/@jetlag?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">David Troeger</a> on <a href="/t/wallpapers?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>

Aber läd das Foto auch wirklich erst _nach_ der eigentlichen Seite und ihrem Content? Ein Blick in den Network-Tab der Firefox Dev-Tools verrät die Antwort: Ja! Die Webseite wird geladen und angezeigt _bevor_ das Bild selbst abgefragt wird.

![](/assets/posts/2021-03-20-browser-network-performance.png)

Möglich wird diese Herangehensweise durch die Javascript-Library [LazySizes](https://github.com/aFarkas/lazysizes/blob/gh-pages/README.md). Alle `<img>`, `<iframe>` oder `<script>` Elemente die mit der Klasse `lazyload` gekennzeichnet werden implementieren lazy loading. Es geht kaum einfacher! 

Aber wie lässt sich diese Herangehensweise in Jekyll nutzen, wenn der Buildhost GitHub Pages ist? Glücklicherweise bietet uns Liquid die Möglichkeit, Markdown-Elemente mit css-Klassen zu versehen. Das obige Bild beispielsweise nutzt folgenden Code:

```html
![](/assets/posts/2021-03-20-%20david-troeger-9XzyEzPAHMI-unsplash.jpg){:class="lazyload"}
```

Die spezifische, optionale Angabe der Klasse ist von mir sehr erwünscht, da ich nicht jedes einzelne Bild auf diese Weise laden möchte, sondern nur sehr große Dateien.