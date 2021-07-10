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

Coder lässt sich dank dem [exzellenten Install-Script](https://raw.githubusercontent.com/cdr/code-server/main/install.sh) sehr einfach per SSH installieren:

```bash
curl -fsSL https://code-server.dev/install.sh | sh
```

Coder bietet nach geglückter Installation an, die Software als Service zu registrieren und zu starten. Es ist empfehlenswert den Service zu starten, da dieser sonst nach Neustart des Servers von Hand per SSH gestartet werden muss. Nach erfolgreichem Start des Dienstes läuft der Coder-Server und lauscht auf `127.0.0.1:808`.


### HTPasswd konfigurieren um das Verzeichnis zu schützen

```bash
sudo htpasswd -c /<gewuenschterPfad>/.htpasswd <username>
```

Nach Eingabe des Befehls kann das Passwort festgelegt, welches dann gehashed abgelegt wird.

### NGINX konfigurieren

Als nächstes konfigurieren wir NGINX um den lokal gehosteten Coder-Server über das Internet erreichbar zu machen. Dazu öffnen wir die bestehende NGINX-Konfigurationsdatei und fügen eine weitere Location hinzu:

```bash
sudo vim /etc/nginx/sites-available/<nameEurerSite>

server {
    # ... Jede Menge Inhalt

    location ^~ /code/ {
        # Basic Auth-Konfiguration
        auth_basic "Only for Unicorns";
        auth_basic_user_file /<pfad>/.htpasswd; # Pfad der im vorherigen Schritt gewählt wurde.

        # Location /code/ auf den lokalen Coder-Server zeigen lassen
        proxy_pass http://127.0.0.1:8080/;

        proxy_http_version 1.1;
        proxy_set_header Connection "upgrade";
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header X-Forward-For $remote_addr;
        proxy_set_header X-Foward-Proto $scheme;

        proxy_read_timeout 1d;
    }

    # ... Jede Menge Inhalt
}

Als nächstes prüfen wir die NGINX-Konfiguration auf (Tipp-)Fehler und starten NGINX neu um die neuen Einstellungen zu übernehmen:

```bash
# Prüfen ob alles korrekt
sudo nginx -T
# NGINX neu starten
sudo systemctl restart nginx
```

Und das wars! 


