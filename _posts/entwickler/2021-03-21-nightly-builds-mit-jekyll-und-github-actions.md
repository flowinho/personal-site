---
title: "How-to: Nightly Builds für Jekyll Blogs mit GitHub Actions umsetzen"
layout: post
tags: .yml
categories: derEntwickler
---

Dieser Post ist eine Art selbst-validierendes Experiment. Geschrieben am 20.03.2021, aber _datiert_ auf den 21.03.2021. Das bedeutet er wird nur im Blog sichtbar, 
wenn heute Nacht, 00:00 GMT+1 die entsprechende GitHub Action aktiv wird und diesen Blog baut. Hoffen wir dass es klappt! 🤞🏻😊

## Warum Nightly Builds für einen Blog?

Die Antwort ist sehr simpel: um Beiträge planen zu können. Jekyll Blogs sind statische Webseiten, die in aller Regel durch einen Githook auf das "Push" Event auf einen Branch, normalerweise `master`, gebaut und deployed werden. Statische Webseiten sind deshalb so toll, weil sie über keinerlei Datenbanken oder sonstiges Backends verfügen, die die Auslieferung oder Anzeige der Seite bremsen könnten. 

Doch statische Webseiten hab auch Nachteile. So lassen sich beispielsweise ohne Continuous Integration bzw. Nightly Builds keine Beiträge einplanen. Denn selbst wenn ein Post, wie dieser hier, ein zukünftiges Datum trägt, wird die statische Seite nur bei jedem Push gebaut. Wer also nicht jede Nacht manuell einen push durchführen möchte, braucht eine Pipeline, die idealerweise Nachts um 00:00 Uhr oder 03:00 Uhr läuft.

Des weiteren eignen sich Jekyll Builds über GitHub Actions besonders gut für GitHub-Pages, da auf diese Weise die von Microsoft definierten Blacklist von Jekyll-Plugins und Ruby-Gems umgehen werden kann.

Dieser Post wird eine solche Pipeline für einen Jekyll Blog mittels GitHub Actions umsetzen, das Prinzip lässt sich aber auf beliebige Integrations-Services ausweiten.

## GitHub Actions + Jekyll = ❤️

GitHub Actions funktioniert sehr straigtforward mittels einer `.yml`-Datei. Wer bereits Berührung mit alternativen Build-Systemen hatte wird diese Form der Konfiguration kennen. Wir starten also in dem wir im Ordner `.github/workflows/` eine neue Datei für unsere Action anlegen, beispielsweise `github-pages.yml`. Die .yml-Datei für diesen Blog kann [hier](https://github.com/flowinho/my-blog/blob/master/.github/workflows/github-pages.yml) eingesehen werden. 

Hier nun der kommentierte Inhalt von `github-pages.yml`:

```yml
{% raw %}name: GitHub Actions Nightly Build

# Das Keyword `on` definiert das Event welches die Action startet.
on:
  push:                     # Sobald ein neuer Commit auf einen beliebigen Branch gepushed wurde.
  schedule:                 # Build mittels cron-Syntax einplanen.
    - cron: "1 6 * * *"     # Morgens, 06:01 Uhr UTC

# Das Keyword `jobs` definiert die auszuführenden Schritte.
jobs:
  jekyll:
    runs-on: ubuntu-16.04   # Zielsystem, ein Docker-Container.
    steps:
    - uses: actions/checkout@v2 # Eine Basis-Action, die es erlaubt Code aus dem Repository 
                                # in dem die Action definiert wurde auszuchecken.

    # Cached den Container um die Buildzeit drastisch zu verkürzen. Erste Build ca 3min, danach ~40s.
    - uses: actions/cache@v2
      with:
        path: vendor/bundle
        key: ${{ runner.os }}-gems-${{ hashFiles('**/Gemfile') }}
        restore-keys: |
          ${{ runner.os }}-gems-

    # Der eigentliche Jekyll Build
    - uses:  helaili/jekyll-action@v2       # Eine GitHub-Action, gewartet von einem Mitglied des Jekyll-Teams.
      with:                                 # Das AccessToken um den Build auszuführen.
        token: ${{ secrets.GITHUB_TOKEN }}{% endraw %}
        target_branch: 'gh-pages'           # Diese Branchspezifikation ist notwendig, um den bestehenden Branch zu überschreiben.
```

Kleines Schmankerl: GitHub Actions zeigt die Auflösung der eingetragenen Cron-Syntax als Popup an.

![](/assets/posts/2021-03-21-github-actions-cron-popover.png)

Nach dem Datei erstellt und befüllt wurde sollten wir sie über "Start Commit" im Webinterface oder einen `git push` ins Repository speichern. Dieser Vorgang führt auch gleich zu einer initialen Ausführung der Action. 

Wer die Actions die diesen Blog bauen in Aktion sehen möchte, kann sie jederzeit gerne [hier](https://github.com/flowinho/my-blog/actions/runs/672710303) betrachten.

Zurücklehnen und genießen!

![](/assets/posts/2021-03-21-github-action-jekyll.png)

Nun muss noch ein evtl. bestehendes GitHub-Pages Environment vom Repository entfernt werden, damit die Action genutzt wird, und nicht das default Environment.

Und wenn alles geklappt hat,  taucht dieser Post morgen in meinem devDiary auf! 🖖🏻