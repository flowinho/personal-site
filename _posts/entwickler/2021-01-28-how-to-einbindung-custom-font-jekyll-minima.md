---
title: "How-to: Einbinden einer eigenen Schriftart in das Jekyll Standard-Thema Minima"
layout: post
tags: scss css
categories: derEntwickler
---

Das Thema Minima welches Jekyll als Grunddesign dient ist sehr schön, allerdings bin ich ein großer Fan der Open-Source Schrift [Hack](https://sourcefoundry.org/hack/). Ich möchte dass dieser Blog in dieser Schriftart erstrahlt, vielleicht nicht alles, zumindest aber die Code-Snippets.

Aufgrund mangelnder Erfahrung mit scss hat das Ganze etwas länger gedauert als erwartet.....

1. Lade Hack auf deinen Computer und extrahiere die Dateien in das Verzeichnis in dem sich dein Jekyll-Blog befindet.
2. Platziere die heruntergeladenen `*.ttf` Dateien in `<deinVerzeichnis>/assets/hack/`. Falls `/assets` nicht existiert, erstelle ihn.
3. Erstelle eine `.scss` Datei die den Namen der einzubindenden Schriftart trägt innerhalb von `_sass`
4. Importiere `hack.scss` in `_sass/minima.scss`.
5. Fertig.

```scss
@import
  "hack",
  "minima/base",
  "minima/layout"
;
```

Inhalt von `hack.scss`:

```scss
@font-face {
  font-family: 'Hack';
  src: local(bttf_font), url('hack/Hack-Regular.ttf') format('opentype');
  font-weight: 400;
  font-style: normal;
} 

@font-face {
  font-family: 'Hack-Bold';
  src: local(bttf_font), url('hack/Hack-Bold.ttf') format('opentype');
  font-weight: 700;
  font-style: normal;
}

@font-face {
  font-family: 'Hack-Italic';
  src: local(bttf_font), url('hack/Hack-Italic.ttf') format('opentype');
  font-weight: 400;
  font-style: italic;
}

@font-face {
  font-family: 'Hack-BoldItalic';
  src: local(bttf_font), url('hack/Hack-BoldItalic.ttf') format('opentype');
  font-weight: 700;
  font-style: italic;
}
```

Kleinere Anpassungen an `prismjs.css` um die Schriftart in Snippets zu verkleinern:

```css
code[class*="language-"],
pre[class*="language-"] {
	// omitted
	font-family: 'Hack', Consolas, Monaco, 'Andale Mono', 'Ubuntu Mono', monospace;
	font-size: 0.9em;
	// omitted
}
```