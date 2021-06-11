---
title: "TestFlight Rejection: Wie grep den Tag rettete"
layout: post
tags: bash zsh grep testflight apple
categories: derEntwickler
---

Heute hatte ich die schöne Gelegenheit einen TestFlight einer App zu betreuen, deren Code-Basis fast ein Jahrzehnt lang gewachsen war.

Solche Apps sind immer interessant. das Besondere an dieser Submission? 

Die Code-Basis wurde, nach einem Rebranding, als neue, zusätzliche App in den Store übertragen.

Doch dann der Schock: 

**Rejected. Reason: Deprecated API usage (UIWebView).**

UIWebView ist ein veraltetes Konstrukt, das seit iOS 12 nicht mehr verwendet werden sollte. Neue Apps dürfen diese Komponente nicht mehr nutzen.

Normalerweise ist sowas kein Aufwand, wäre da nicht ein Problem: die App verwendet überhaupt keine UIWebViews.

Wo kam der Fehler also her? Eine Suche innerhalb des Projekts ergab keine Treffer, also war klar, dass sich UIWebView innerhalb einer der statischen Bibliotheken befinden muss. 

Und hier kam `grep` zur Hilfe! Es ist in der Lage auch binäre Dateien zu durchsuchen.

```bash
grep -r UIWebView .
```

Die Eingabe dieses Befehls im Projektverzeichnis offenbarte, dass sich die UIWebView in einer alten Integration des PayPal-iOS-SDK befand.

In Momenten wie Diesem erinnere ich mich gerne an meinen alten Chef von Zeitland, der mich maßgeblich dazu motivierte meine Terminal-Kenntnisse zu vertiefen.

Danke, Mic 🍻