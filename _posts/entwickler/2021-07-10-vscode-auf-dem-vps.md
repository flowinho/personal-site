---
title: "Ubuntu: Visual Studio Code auf dem eigenen VPS hosten"
layout: post
tags: vscode vps coder-server ubuntu
categories: derEntwickler
---

Vor bier bis fünf Jahren, mit dem ersten iPad Pro, kam bei mir der Wunsch auf, mobil zu entwickeln. Sicherlich ist vor allem Apple mit Schuld daran, dass ich dieses Ziel über Jahre hinweg verfolgt habe -- schließlich wurde es als *der* Ersatz für den Computer beworben. Damals, wie teilweise heute, fällt das Ergebnis eher ernüchternd aus. Swift Playgrounds ist noch nicht so niet und nagelfest wie es sein könnte, und obwohl iOS 15 die Möglichkeit bringen wird, eigene Apps direkt aus Playgrounds in den AppStore zu veröffentlichen, bleiben viele Erwartungen an das iPad als Gerät zur Softwareentwicklung vorerst unangesprochen.

Nun gibt es eine Firma namens [Coder](https://coder.com/), die ihr Geld mit Browser-basierten Entwicklungsumgebungen verdient. Im Rahmen meiner Beschäftigungen habe ich hier und da Berührungspunkte mit deren Diensten gehabt, bin aber nicht auf die Idee gekommen, ganze IDEs selbst zu hosten. 

## Visual Studio Code selbst hosten

![](/assets/posts/derEntwickler/2021-07-10-vscode/vscode-ipad.JPG)

Ist das nicht mega stark? Im Folgenden möchte ich euch erklären wie ihr zum selben Ergebnis kommen könnt wie ich.

### Vorraussetzungen

- Ein VPS mit SSH Zugang und einen User der über sudo-Rechte verfügt und Software installieren darf.
- Ubuntu Server 18 oder höher.
- NGINX sollte bereits eingerichtet sein und mit Let's Encrypt gesichert worden sein. Vorwissen bezüglich NGINX-Konfigurationen sollte vorhanden sein.
- Coder empfiehlt 1GB RAM, *obwohl ich das so nicht bestätigen kann*.

Das Ziel dieses Artikels:

- Coder installieren und über den Reverse-Proxy NGINX ausliefern.
- Sicherung von Coder durch HTTP-Basic-Auth.

Beginnen wir mit den Grundeinstellungen:

```bash
# Alle Pakete aktualisieren
sudo apt update && sudo apt upgrade -y

# Apache-Utils installieren um htpasswd nutzen zu können
sudo apt install apache2-utils
```

Damit wäre unser System bereit.

### Coder installieren

Coder lässt sich dank dem [exzellenten Install-Script](https://raw.githubusercontent.com/cdr/code-server/main/install.sh) sehr einfach installieren:

```bash
curl -fsSL https://code-server.dev/install.sh | sh
```

Coder bietet nach geglückter Installation an, die Software als Service zu registrieren und zu starten. Es ist empfehlenswert den Service zu starten, da dieser sonst nach Neustart des Servers von Hand per SSH gestartet werden muss. Nach erfolgreichem Start des Dienstes läuft der Coder-Server und lauscht auf `127.0.0.1:808`.

### NGINX konfigurieren




