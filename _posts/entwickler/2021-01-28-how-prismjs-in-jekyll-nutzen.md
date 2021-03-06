---
title: "How-to: Prims.js innerhalb eines Jekyll blogs nutzen"
layout: post
tags: html css
categories: derEntwickler
---

Ein sehr kurzes How-To welches kurz erläutern soll, wie man [prismjs](https://prismjs.com) in einen Blog integriert der auf Jekyll basiert.

1. Konfiguriere dein Paket und lade es herunter.
2. Kopiere die Dateien in deinen Jekyll blog.
3. Importiere das Stylesheet und Javascript im `<head>` Element deiner Website.

Ein Beispiel:

```html
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="{{ "/assets/main.css" | relative_url }}">
    <link rel="stylesheet" href="{{ "/prism/prism.css" | relative_url }}">
    <script src="/prism/prism.js"></script>
  </head>
  
```

Optional: Einstellung der Schriftgröße in prism.css.
```css
code[class*="language-"],
pre[class*="language-"] {
	color: black;
	background: none;
	text-shadow: 0 1px white;
	font-family: Consolas, Monaco, 'Andale Mono', 'Ubuntu Mono', monospace;
	font-size: 0.9em;   // war 1em
	text-align: left;
	white-space: pre;
	word-spacing: normal;
	word-break: normal;
	word-wrap: normal;
	line-height: 1.5;

	-moz-tab-size: 4;
	-o-tab-size: 4;
	tab-size: 4;

	-webkit-hyphens: none;
	-moz-hyphens: none;
	-ms-hyphens: none;
	hyphens: none;
}
```