---
title: "Meine Backup-Strategie für WordPress-Websiten"
layout: post
tags: wordpress xcloner nextcloud webdav
categories: derEntwickler
---

Was ist der erste Schritt zu einer neuen Website, nachdem man sich für ein CMS (Content-Management-System) entschieden hat? Dieses installieren. In manchem Falle WordPress 5.

Was ist der zweite Schritt zu einer neuen Website, nachdem man das CMS installiert hat? Ein Backup einrichten.

Backup. Backup.

Backup.

> Ein Backup ist kein Backup — und zwei Backups sind ein Backup.

Was Prof. Dr. Ertel damals wiedergab, ist einer der Kernweisheiten der Informationstechnologie und sollte für jedes System gelten, mit dem man in Berührung kommt, egal ob komplexes System welches eine professionelle Anwendung findet oder privates Laptop. Genau deshalb gilt dieses Credo selbstverständlich auch für Websites.

Idealerweise arbeitet dieses Backup automatisiert, denn manuell ausgeführte Backups werden erfahrungsgemäß nicht regelmäßig genug ausgeführt.

Zusätzlich zur Automatisierung ist erstrebenswert das Backup auf ein Speichermedium genauer gesagt einen Speicherort zu legen, der unter der eigenen Kontrolle und auch dem Datenschutzrecht des eigenen Landes unterliegt. **Dieser Speicherort sollte ebenfalls über automatische Backups gesichert sein.** Denn wie wir alle wissen: Ein Backup ist kein Backup.

Manche Seite nutzt WordPress, welches mir ermöglicht das meiner Erfahrung nach gute Plug-in XCloner zu nutzen. Details dazu findet ihr auf der Plug-in-Seite: [https://de.wordpress.org/plugins/xcloner-backup-and-restore/](https://de.wordpress.org/plugins/xcloner-backup-and-restore/)

Warum ich XCloner mag und gerne empfehle:

- Die Benutzerführung ist sehr einfach gehalten und damit sehr zugänglich.
- Es unterstützt WebDAV, und ist damit mit Nextcloud-Instanzen kompatibel.
- Es bietet die Möglichkeit Verzeichnisse oder einzelne Dateien vom Backup-Vorgang auszuschließen. Das ist wichtig, um sehr kleine Backups zu erzeugen, welche sich wesentlich besser archivieren lassen, da diese Archive nur das Minimum an relevanten Daten beinhalten.
- Es bekommt recht schnell Updates, um kompatibel mit aktuellen WordPress-Versionen zu bleiben.
- XCloner kann, falls gewünscht, über den Status des letzten Backups per E-Mail informieren. Das ist besonders relevant für Nutzer die mehrere WordPress-Instanzen betreiben oder betreuen.

## Konfiguration von Nextcloud

Es ist wichtig für diese Backup-Vorgänge einen eigenen User in der Nextcloud Administrationsoberfläche anzulegen.

Warum?

- Ein User-Account sollte nicht von automatisierter Software gefüllt werden, da Fehlfunktionen möglicherweise großen Einfluss auf diesen Account haben. Es ist eine etablierte Herangehensweise für automatisierte Aufgaben sogenannte „technische Nutzer“ anzulegen, um den Einfluss auf produktiv genutzte User-Accounts nicht negativ zu beeinträchtigen.
- Wird ein technischer Nutzer statt ein echter Nutzer verwendet, lassen sich dessen Zugriffsrechte besser regeln.
- Der Nutzer wird nicht mit automatisierten Backups „zugemüllt“. Wer will das schon?
- Sowohl bei WordPress als auch bei XCloner handelt es sich um „Fremd-Software“ die selbst schadhaft sein kann, oder durch Sicherheitslücken angreifbar werden könnte. Durch das Anlegen eines technischen Nutzers wird die Gefahr einer Kompromittierung der Nextcloud durch WordPress oder XCloner reduziert.

Idealerweise wird das Speicherkontingent des technischen Nutzers eingeschränkt, bei mir wäre das 1 Gigabyte.

Nachdem der technische Nutzer angelegt wurde, wird die WebDAV-URL dieses Nutzers benötigt um XCloner korrekt konfigurieren zu können. Prinzipiell ist das Format der WebDAV-Url eines Nextcloud-Nutzers nach folgendem Schema definiert:

https://<url-der-cloud>/remote.php/dav/files/<nutzername>

Alternativ kann die WebDAV-Url im Webinterface gefunden werden – dazu die Einstellungen der Nextcloud in der linken unteren Ecke einblenden.

## Konfiguration von XCloner

Nachdem Nextcloud nun konfiguriert ist als nächstes XCloner an der Reihe.
Storage Locations

Im Reiter „Storage Locations“ bietet XCloner mehrere Optionen. Da sich dieser Artikel auf Nextcloud konzentriert ist der Bereich WebDAV relevant.

Eine Beispielkonfiguration für einen technischen Nutzer der Nextcloud-Instanz „https://meine.private-wolke.de“ könnte folgendermaßen aussehen:

```bash
WebDAV Base URL: https://meine.private-wolke.de/remote.php/dav/files/wordpress/
WebDAV Username: technischerNutzer
WebDAV Target Path: 
Cleanup by Age: 90
Cleanup by Quantity: 10
Cleanup by Capacity: 1024
Keep backups taken on days:
```

Nach einem Klick auf „Save“ sollte nicht vergessen werden die WebDAV Storage Location auch auf On zu stellen.

Im Bereich „Generate Backups“ kann man das Ganze dann testen

## Reiter: Backup Options

- Eine Verschlüsselung des Backups ist nicht zwingend erforderlich, kann aber optional aktiviert werden. Da es sich beim Speicherort des Backups um eine selbst betriebene Nextcloud handelt kann davon ausgegangen werden dass sie vertrauenswürdig ist.
- Im Feld Send to remote storage: den zuvor konfigurierten Speicherort WebDAV wählen.

## Reiter: Database Options

Hier einfach alle Datenbanken auswählen die für ein Backup relevant und / oder interessant wären. Im Normalfall sollten hier alle Datenbanken gewählt werden.

## Reiter: Files Options

Der Bereich Files Options böte die Möglichkeit Verzeichnisse und / oder Dateien explizit vom Backup auszuschließen.

Im Normalfall, also einer Standard-Installation sollte dies nicht notwendig sein.

## Reiter: Schedule Backup

Dieser Reiter bietet die Möglichkeit regelmäßige Backups in einem Zeitplan zu hinterlegen. Diese Vorgehensweise ist absolut zu empfehlen, da manuell ausgeführten Backups oft eine gewisse Regelmäßigkeit fehlt.

Idealerweise einmal wöchentlich.

Das war’s! Ich hoffe ich konnte euch mit diesem Artikel weiterhelfen und aufzeigen wie einfach es sein kann automatisierte Backups der eigenen WordPress-Seite umzusetzen.