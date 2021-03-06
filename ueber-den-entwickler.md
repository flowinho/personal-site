---
layout: page
title: "Über den Entwickler"
uikit-icon: "git-branch"
permalink: /ueber-den-entwickler/
---

![](/assets/entwickler/office.jpg)

Jepp, ich programmiere diese Apps für euer iPhone <span uk-icon="phone"></span>. Apps, das sind kleine Programme mit großer Logik. Warum ich das seit grob 2013 mache? Damit ihr das nicht machen müsst! Und weil es mir wichtig ist, dass die Programme auf allen Endgeräten dasselbe für die Nutzer tun, fokussiere ich mich auf Apple-Geräte. 

Neben meiner Tätigkeit als iOS-Entwickler tüftel ich auch gerne an verschiedenste anderen Technologien herum, die meistens was mit diesem ominösen "Internet" zu tun haben, ein Beispiele dafür ist [diese Website](/ueber-diese-seite/).

Meine iOS-spezifischen Kenntnisse fließen in den Podcast [Audiodump](https://audiodump.de) ein -- ich versuche dort, mal mehr, mal weniger verzweifelt, so manchen komplizierten Sachverhalt möglichst einfach zu erläutern.

<div class="uk-alert-warning" uk-alert>
    <a class="uk-alert-close" uk-close></a>
    <p><span uk-icon="warning"></span> Aufgrund meiner aktuellen Beschäftigung stehe ich nicht für Auftragsarbeiten zur Verfügung.</p>
</div>

Ganz selten haben mich meine Kolleg:innen auf der Backend-Seite <span uk-icon="database"></span> eines Projekts gesehen, aber nur wenige haben diese Erfahrung überlebt.
<br /><br />

<div class="" uk-grid>
    <div class="uk-width-expand@m">
    <h3>Meine Motivation hinter der Software-Entwicklung</h3>
    <ul>
        <li>Programmieren, also die Tätigkeit Code zu erzeugen, ist der Output des Software-Konzepts, der Architektur der Software, und der festgelegten Paradigmen und Code Conventions.</li>
        <li>Wir coden für Menschen - nicht Maschinen. Source Code muss menschenlesbar sein, um wartbar und erweiterbar zu sein. Es sollte immer im Hinterkopf bleiben, dass der Entwickler der diesen Code in ein paar Monaten anschauen muss evtl. man selbst ist. Lesbarer Code ist guter Code - Funktionalität lässt sich nur dann optimieren, wenn der Quellcode an sich zugänglich ist.</li>
        <li>Es gibt keinen fehlerfreien Code. Fehler zu akzeptieren und zu beseitigen ist Teil des Alltags. Es muss professionelles Verständnis sein, dass der Hinweis auf fehlerhafte Implementierungen kein fehlender Respekt ist, sondern der gemeinsame Drive, besser zu werden.</li>
        <li>Objektorientierung ist ein in manchen Fällen überholtes Modell, hat aber ihre Daseinsberechtigung. Sie sollte aber nicht willkürlich eingesetzt werden, "weil man das halt so macht", oder gar nicht anders kennt.</li>
    </ul>
    </div>
    <div class="uk-width-1-3@m">
    <h3>Randnotizen</h3>
    <ul>
        <li>Scrum funktioniert</li>
        <li>Arc42 generiert Mehrwert</li>
        <li>SAFe funktioniert</li>
        <li>Composition over Inheritance</li>
        <li>Sicherheit ohne Transparenz, ohne Open Source, ist eine Lüge</li>
        <li>Abstraktion > Konkretisierung</li>
    </ul>
    </div>
</div>
<br />
Oder um es anderes auszudrücken:
> Programmierer lösen gerne die Probleme, die Sie gerne hätten -- nicht zwangsläufig die Probleme, die Sie wirklich haben.
*Unbekannter Author, leider allzu wahr.*

<h2 class="uk-heading-line"><span>Nebenprojekt: Ladefuchs -- Einfach schlau laden</span></h2>

<div class="" uk-grid>
    <div class="uk-width-1-3@m" uk-lightbox="animation: slide">
    <a class="uk-inline" href="/assets/entwickler/ladefuchs.png" data-caption="Ladefuchs iOS (links) und Android (rechts)">
            <img src="/assets/entwickler/ladefuchs.png" alt="">
        </a>
    </div>
    <div class="uk-width-expand@m">
        <div uk-alert>
            <p>WAS KOSTET DER STROM FÜR DEIN E-AUTO? <br />
                Blitzschnell die günstigste Ladekarte finden. Mit einem Fingerwischen zeigt Dir der Ladefuchs die günstigste Ladekarte an der Elektro-Ladesäule. <br />
                Nicht mehr, nicht weniger. </p>
        </div>
        <span class="uk-text-muted">Beschreibung der App, übernommen von <a href="https://ladefuchs.app">https://ladefuchs.app</a>.</span><br /><br />
        <ul>
            <li>Ladefuchs ist ein Kooperationsprojekt von Mitgliedern der Podcasts <a href="https://www.cleanelectric.de/">Clean Electric</a>, <a href="http://www.bitsundso.de/category/podcast/">Bits und so</a> und <a href="https://audiodump.de">Audiodump</a>.</li>
            <li>Die App ein Geschenk an alle Fahrer von Elektro-Fahrzeugen, die gesamte EV-Community und alle Hörer unserer Podcasts und wird unentgeltlich von uns entwickelt.</li>
            <li>Ladefuchs-Strompreise werden durch eine Kooperation mit <a href="https://www.chargeprice.app/">ChargePrice</a> zur Verfügung gestellt.</li> 
            <li>Mein Beitrag zum Ladefuchs ist die Entwicklung der iOS-App.</li>
        </ul>
        Weitere Informationen zu diesem Projekt finden sich <a href="https://ladefuchs.app">hier.</a><br /><br />
        <span class="uk-badge">swift</span>
        <span class="uk-badge">xcode</span>
        <span class="uk-badge">alamofire</span>
        <span class="uk-badge">swiftyJSON</span>
    </div>
</div>

<h2 class="uk-heading-line"><span>Nebenprojekt: derflo.io -- Meine persönliche Website</span></h2>

<div class="" uk-grid>
    <div class="uk-width-expand@m">
        <p> Webseiten sollten performant, leichtgewichtig und ohne Tracking versehen sein. Idealerweise funktionieren Sie ohne Datenbanken und lassen sich über GIT versionieren. Durch den Verzicht auf Trackung und dank Jekyll erfüllt dieses Projekt die genannten Kriterien.
        <br />
        <br />
        Das Projekt ist Open Source, um der Community etwas zurückzugeben. 
            <ul>
                <li>Erstellt mit <a href="https://jekyllrb.com">Jekyll</a> und <a href="https://getuikit.com">UIKit</a>.</li>
                <li>Diese statische Website wird bei jedem Push, aber mindestens jede Nacht durch eine <a href="https://github.com/features/actions">GitHub Action</a> gebaut und deployed.</li>
                <li>Gehostet wird die Seite auf <a href="https://github.com">GitHub</a>, spezifischer <a href="https://pages.github.com/">GitHub Pages</a>.</li>
            </ul>
        Weitere Informationen zu diesem Projekt finden sich <a href="/ueber-diese-seite/">hier</a>, der Quellcode <a href="https://github.com/flowinho/personal-site">hier.</a>
        </p> 
        <span class="uk-badge">jekyll</span>
        <span class="uk-badge">liquid</span>
        <span class="uk-badge">html</span>
        <span class="uk-badge">javascript</span>
        <span class="uk-badge">github actions</span>
    </div>
    <div class="uk-width-1-3@m" uk-lightbox="animation: slide">
    <a class="uk-inline" href="/assets/entwickler/ipad-screen-flowinhocom.png" data-caption="flowinho.com auf einem iPad Air 2020">
            <img src="/assets/entwickler/ipad-screen-flowinhocom.png" alt="">
        </a>
    </div>
        
</div>

<h2 class="uk-heading-line"><span>Nebenprojekt: Virtual Private Server</span></h2>

<div class="" uk-grid>
    <div class="uk-width-1-4@m" uk-lightbox="animation: slide">
        <a class="uk-inline" href="/assets/entwickler/vps.PNG" data-caption="htop auf dem VPS">
            <img src="/assets/entwickler/vps.PNG" alt="">
        </a>
    </div>
    <div class="uk-width-expand@m">
    <br />
    <p>Seit Anfang des Jahres 2020 betreibe ich beim Hoster <a href="https://contabo.de">Contabo</a> meinen eigenen kleinen Server zu privaten Zwecken. Einen eigenen Server zu Betreiben ist eine Herausforderung, der ich mich gerne stelle, insbesondere im Security-Bereich.<br /><br /></p>
    <div class="" uk-grid>
        <div class="uk-width-expand@m">
            Dieser Server stellt einen Lernbereich für mich dar, denn Nutzen und Lernen lassen sich hier optimal verbinden, zum Beispiel:
            <br /><br />
            <ul>
                <li>Absicherung der Remote Shell des VPS, u.a. über sshd_config und <a href="https://www.fail2ban.org/wiki/index.php/Main_Page">fail2ban</a>.</li>
                <li>Konfiguration von DNS-Zonen um den VPS über eine Domain erreichbar zu machen.</li>
                <li>Betrieb des Reverse-Proxy <a href="https://www.nginx.com/">nginx</a> um lokale Services abzusichern.</li>
                <li>Konfiguration von <a href="https://letsencrypt.org/de/">certbot (Let's Encrypt)</a> und nginx um Webservices mit HTTPS abzusichern.</li>
                <li>Konfiguration und Betrieb von Containern über <a href="https://www.docker.com/">docker</a> und <a href="https://docs.docker.com/compose/">docker-compose</a>.</li>
                <li>Betrieb des modernen IRC-Clients und Bouncers <a href="https://github.com/thelounge/thelounge">The Lounge</a>.</li>
            </ul>
        </div>
        <div class="uk-width-1-4@m">
            <h3>Eckdaten</h3>
            <ul>
                <li>4 vCPU</li>
                <li>8 GB RAM</li>
                <li>200 GB SSD</li>
            </ul>
        </div>
    </div>    
    
    <br />

    <span class="uk-badge">ubuntu</span>
    <span class="uk-badge">ufw</span>
    <span class="uk-badge">OpenSSH</span>
    <span class="uk-badge">fail2ban</span>
    <span class="uk-badge">nginx</span>
    <span class="uk-badge">docker</span>
    <span class="uk-badge">lets encrypt</span>
    </div>
</div>

<h2 class="uk-heading-line"><span>Elevator CV</span></h2>

<span class="uk-text-muted">Die unten aufgelisteten Themen und Technologien sind unvollständig. Weitere Details dürfen aus Compliance-Gründen nicht genannt werden.</span>

<div class="uk-child-width-1-2@s uk-grid-collapse uk-text-center" uk-grid>
    <div>
        <div class="uk-tile uk-tile-default">
            <p class="uk-h3 uk-text-primary">Robert Bosch GmbH</p>
            <span class="uk-text-muted">iOS Software-Engineer, 2018 - Heute</span>
            <div align="left">
            <ul>
                <li>Analyse, technisches Konzept und Umsetzung von Apps in den Themenfeldern:</li>
                <ul>
                    <li>Corporate Mobility</li>
                    <li>eBike</li>
                    <li>Automated Valet Parking</li>
                    <li>Charging Infrastructure</li>
                </ul>
                <li>Implementierung CI/CD-Pipelines mehrere Apps mit MS Azure DevOps und MS AppCenter. </li>
                <li>Mitglied in der Gilde "Continous Integration".</li>
                <li>Mitarbeit in SAFe Teams zwischen 50 und 120+ Teammitgliedern.</li>
                <li>Schnittstelle App-Entwicklung<span uk-icon="triangle-left"></span><span uk-icon="triangle-right"></span>UX.</li>
                <li>Weitere Inhalte folgen nach Freigabe.</li>
            </ul>
            </div>
            <span class="uk-badge">swift</span>
            <span class="uk-badge">objective-c</span>
            <span class="uk-badge">azure devops</span>
            <span class="uk-badge">ms appcenter</span>
            <span class="uk-badge">yaml</span>
            <span class="uk-badge">oauth2</span>
            <span class="uk-badge">cocoapods</span>
            <span class="uk-badge">carthage</span>
            <span class="uk-badge">adobe photoshop</span>
            <span class="uk-badge">adobe xD</span>
        </div>
    </div>
    <div>
        <div class="uk-tile uk-tile-muted">
            <p class="uk-h3">myScotty</p>
            <span class="uk-text-muted">iOS Software-Engineer, 2017 - 2018</span>
            <div align="left">
            <ul>
            <li>Integration neuer Features in die App des Start-Ups.</li>
                <li>Implementierung CI/CD-Pipeline für die App des Start-Ups.</li>
                <li>Einführung von OKR in das Unternehmen.</li>
                <li>Koordination des iOS-Entwicklerteam in Ludwigsburg (DE) und Cluj-Napoca (RO).</li>
                <li>Anpassung der iOS-Softwarearchitektur um Wartbarkeit, Testbarkeit und Zuverlässigkeit zu erhöhen.</li>
                <li>Schnittstelle App-Entwicklung<span uk-icon="triangle-left"></span><span uk-icon="triangle-right"></span>UX.</li>
            </ul>
            </div>
            <span class="uk-badge">swift</span>
            <span class="uk-badge">objective-c</span>
            <span class="uk-badge">azure devops</span>
            <span class="uk-badge">ms appcenter</span>
            <span class="uk-badge">yaml</span>
            <span class="uk-badge">cocoapods</span>
            <span class="uk-badge">adobe photoshop</span>
            <span class="uk-badge">adobe xD</span>
        </div>
    </div>
    <div>
        <div class="uk-tile uk-tile-muted">
            <p class="uk-h3">Zeitland media & games GmbH</p>
            <span class="uk-text-muted">Technical Director, 2014 - 2017</span>
            <div align="left">
            <ul>
                <li>Implementierung von cross-platform Apps und Videospielen in Microsoft Xamarin bzw. Unity3D.</li>
                <li>Lead-Entwicklung native iOS-Entwicklung u.a. im Pharma-Bereich.</li>
                <li>Unterstützung unserer Kunden bei der Verteilung von Apps innerhalb ihres Unternehmens.</li>
            </ul>
            </div>
            <span class="uk-badge">swift</span>
            <span class="uk-badge">objective-c</span>
            <span class="uk-badge">c#</span>
            <span class="uk-badge">cocoapods</span>
        </div>
    </div>
    <div>
        <div class="uk-tile uk-tile-default">
            <p class="uk-h3">Selbstständiger Unternehmer</p>
            <span class="uk-text-muted">2013 - 2014</span>
            <div align="left">
            <ul>
                <li>Native iOS-Entwicklung.</li>
                <li>Unterstützung in Konzept und Entwurf von Software-Oberflächen.</li>
                <li>Unterstützung meiner Kunden bei der Verteilung von Apps innerhalb ihres Unternehmens.</li>
            </ul>
            </div>
            <span class="uk-badge">objective-c</span>
            <span class="uk-badge">adobe photoshop</span>
        </div>
    </div>
</div>

## Für Fans von Listen

<div class="uk-grid-divider" uk-grid>
    <div class="uk-width-1-4@m">
    <h4>Programmiersprachen</h4>
    <ul>
        <li>Swift</li>
        <li>Objective-C</li>
        <li>YAML</li>
        <li>LaTeX</li>
        <li>C#</li>
        <li>HTML</li>
        <li>CSS</li>
        <li>Shellscripts</li>
    </ul>
    </div>
    <div class="uk-width-1-4@m">
    <h4>Tools</h4>
    <ul>
        <li>Apple Xcode</li>
        <li>JetBrains AppCode</li>
        <li>Carthage</li>
        <li>Cocoapods</li>
        <li>Adobe Photoshop</li>
        <li>Adobe xD</li>
        <li>Microsoft Xamarin.iOS</li>
        <li>Unity3D</li>
        <li>Jekyll</li>
        <li>Homebrew</li>
        <li>VSCode</li>
        <li>GIT</li>
    </ul>
    </div>
    <div class="uk-width-1-4@m">
    <h4>Corporate</h4>
    <ul>
        <li>SAFe & Scrum</li>
        <li>Atlassian Bitbucket</li>
        <li>Atlassian Jira</li>
        <li>Atlassian Confluence</li>
        <li>GitHub Enterprise</li>
    </ul>
    </div>
    <div class="uk-width-1-4@m">
    <h4>Administration</h4>
    <ul>
        <li>Nextcloud</li>
        <li>MS AppCenter</li>
        <li>MS Azure DevOps</li>
        <ul>
            <li>Teams</li>
            <li>Projekte</li>
            <li>Pipelines</li>
            <li>SCM Policies</li>
        </ul>
    </ul>
    </div>
</div>

<br /> <br />
Am 05.05.2021 habe ich meine bestehenden StackOverflow-Accounts eingestampft und einen neuen, korrekten Account erstellt.

<a href="https://stackoverflow.com/users/15840803/flowinho"><img src="https://stackoverflow.com/users/flair/15840803.png" width="208" height="58" alt="profile for Flowinho at Stack Overflow, Q&amp;A for professional and enthusiast programmers" title="profile for Flowinho at Stack Overflow, Q&amp;A for professional and enthusiast programmers"></a>