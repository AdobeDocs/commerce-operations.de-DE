---
title: Best Practices bei der Codeüberprüfung
description: Erfahren Sie mehr über die Best Practices zur Codeüberprüfung für die Entwicklungsphase von Adobe Commerce-Projekten.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 0%

---


# Best Practices zur Codeüberprüfung für Adobe Commerce

Das Hauptziel der Codeüberprüfung besteht darin zu überprüfen, ob die implementierte Funktionalität die Anforderungen aus Performance-, Architektur- und Sicherheitsperspektiven optimal erfüllt.

Darüber hinaus soll durch die Codeüberprüfung sichergestellt werden, dass der Code die Best Practices für die Adobe Commerce-Entwicklung erfüllt, leicht zu verstehen und zu pflegen ist und den Kodierungsstandards entspricht. Die meisten Codierungsstandards sollten von entsprechenden Tools automatisch überprüft werden.

## Empfohlener Code-Überprüfungsprozess

Auf hoher Ebene sollte der Code-Überprüfungsprozess aus folgenden Schritten bestehen:

1. Checkout-Funktionsverzweigung in der lokalen Entwicklungsumgebung.
1. Wenn es seit dem Übermitteln des Codes noch nicht so lange her ist, führen Sie die neuesten Änderungen aus der Zielverzweigung (normalerweise QA-Verzweigung) zusammen und pushen Sie Aktualisierungen an die Remote-Funktionsverzweigung (falls vorhanden).
1. Führen Sie eine allgemeine Überprüfung durch, um zu überprüfen, ob der Code alle Anforderungen implementiert. Wenn es große Diskrepanzen gibt, wenden Sie sich zur Klärung an den Entwickler.
1. Das Ausführen des Codes ist optional. Wenn Sie jedoch Zweifel haben, ob der Code erwartungsgemäß funktioniert oder die Effizienz des Prozesses erleichtert, testen Sie, ob die implementierte Funktionalität in den Hauptanwendungsszenarien erwartungsgemäß funktioniert. Wenn es wichtige Probleme gibt, stoppen Sie den Überprüfungsprozess und öffnen Sie das Ticket mit den entsprechenden Kommentaren erneut.
1. Führen Sie eine gründliche Überprüfung durch, um zu überprüfen, ob der Code alle Anforderungen implementiert. Wenn Probleme auftreten, fügen Sie der Pull-Anforderung entsprechende Kommentare hinzu und öffnen Sie das Ticket erneut.
1. Wenn alles gut aussieht, führen Sie die Pull-Anforderung zusammen (oder übergeben Sie sie an die nächste Code-Überprüfungsebene, falls eine festgelegt wurde).

Beachten Sie außerdem die folgenden Punkte bei der Implementierung von Code-Überprüfungsprozessen:

- Die Codeüberprüfung ist ein primäres Werkzeug für die Kommunikation und den Wissenstransfer innerhalb eines Teams. Selbst wenn eine Pull-Anforderung keine größeren Probleme enthält und die erforderliche Geschäftslogik implementiert, können Sie sie als Möglichkeit nutzen, weitere Verbesserungen nach der Zusammenführung vorzuschlagen.

- Im Durchschnitt sollte die Codeüberprüfung nicht mehr als 10 % bis 20 % der Entwicklungsbemühungen erfordern. Das setzt voraus, dass das Entwicklungsteam aus leitenden Ingenieuren besteht, die gut zusammenarbeiten. Wenn die Codeüberprüfung länger dauert, kann sich dies auf das Projektbudget und die Timeline auswirken.

- Beheben Sie Probleme mit übermäßigem Aufwand für Codeüberprüfungen, indem Sie die Grundursache ermitteln. Normalerweise liegt das daran, dass entweder Anforderungen schlecht in Entwicklungstickets übersetzt werden (aufgrund von Kommunikationsproblemen, schlechten Benutzergeschichten) oder dass es sich um ein Coaching-Problem handelt. Im ersten Fall wird empfohlen sicherzustellen, dass Tickets über genügend Informationen verfügen, damit Teammitglieder die Anforderungen effizient erfüllen können. Im zweiten Fall müssen Sie möglicherweise die Teamstruktur so anpassen, dass mehr Senior Engineers einbezogen werden, oder Sie müssen die Genehmigung außerhalb von Mentoring und Coaching erhalten.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Suchen in der Codeüberprüfung

### Stil

Der Stil kann automatisch getestet werden, indem die PhpStorm-Inspektion ausgeführt wird (siehe unten).

Konfigurieren Sie unbedingt [PHPMD und PHPCS](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) und zum Ausführen der [Codierungsstandard](https://github.com/magento/magento-coding-standard) -Tool aus der CLI (auch unten). Es gibt einige Überschneidungen, aber beide haben auch eindeutige Tests.

### Übereinkommen und Struktur

Die Überprüfungen der Konvention und der Struktur werden manuell durchgeführt.

- Ist die Klassenfunktionalität auf eine einzige Verantwortung beschränkt?
- Ist die Verzeichnisstruktur sinnvoll?
- Die Funktionalität wird auf der richtigen Ebene ausgeführt (Server, Client, CSS, JS, Datenbank, Framework, Infrastruktur).
- Ist die Versionierung korrekt?
- Sieht der Code unkonventionell aus oder versucht er, ein Problem auf die falsche Weise zu lösen?
- Wird die Namenskonvention für Modulname, Paketname und Repository-Name korrekt angewendet?
- Vergewissern Sie sich, dass globale CSS-Stile sorgfältig angewendet werden und nicht zu häufig verwendet werden.

### Vollständigkeit

Die Überprüfung der Vollständigkeit erfolgt manuell.

- Kann der Code durch Konfiguration aktiviert oder deaktiviert werden und verhält sich der gesamte erforderliche Code erwartungsgemäß?
- Ist die gesamte Konfiguration vorhanden, die im Ticket erwähnt wird? Überprüfen Sie Umfang, Datentyp, Validierung, Übersetzung und Standardwerte.
- Wird die Konfiguration immer auf der niedrigstmöglichen Ebene abgerufen (Store-Ansichtsebene, Website-Ebene oder globale Ebene)? Der Konfigurationsabruf muss mit der Definition des Umfangs im Abschnitt `system.xml` -Datei.
- Werden alle Pfade im Flussdiagramm der technischen Spezifikation abgedeckt? Werden alle anderen technischen Spezifikationen berücksichtigt?
- Sind ACLs für die neue Funktion definiert?
- Sind PhpDocs klar? Sind Commit-Nachrichten klar?
- Ist Code auskommentiert oder wird Debugging-Code angezeigt?

### Leistung

Die Überprüfung der Leistung erfolgt manuell, was im Zweifelsfall durch die Codeausführung unterstützt werden kann.

- Werden Abfragen in einer Schleife ausgeführt? Diese Schleife kann sich außerhalb der bearbeiteten Dateien befinden.
- Können Sie beliebige `cachable="false"` Attribute? Werden sie korrekt angewendet?

### Sicherheit

Sicherheitsprüfungen werden manuell durchgeführt, was durch die Textsuche unterstützt werden kann. Ein Teil der Sicherheitsprüfung wird durch automatisierte Tests durchgeführt.

- Werden bei Bedarf Ausnahmen protokolliert? Werden die richtigen Arten von Ausnahmen verwendet?
- can `around` Plug-ins vermieden werden?
- Gibt das Plug-in die richtigen Datentypen zurück?
- Können Sie Raw-SQL-Abfragen finden, die mithilfe der Datenbank-Abstraktionsebene erstellt werden sollen?
- Sind neue Datentypen für beliebige Benutzer, Administratoren oder Frontend verfügbar? Ist diese Risikoposition ein Sicherheitsrisiko?
- Werden benutzergenerierte Daten validiert? Alles, was aus dem Browser stammt, gilt als vom Benutzer generiert, einschließlich Cookie-Werten und Server-Headern.

### Datenschutz und DSGVO

Überprüfungen der Privatsphäre und [DSGVO](../../../security-and-compliance/privacy/gdpr.md) manuell ausgeführt werden.

- Verarbeitet der Code Kundendaten oder E-Mails? Achten Sie besonders darauf.
- Wenn dieser Code in einer Schleife ausgeführt werden kann, kann er dann die Kundendaten von einem Schleifenzyklus zum anderen übergeben?
- Indikatoren für ein Risiko sind Importe, Cron-Aufträge, Transaktions-E-Mails und Batch-Warteschlangen-Handler.
- Sicherstellen der Isolierung von Benutzerdaten in Schleifen. Adobe empfiehlt, Fabriken oder Repositorys zu verwenden, um Modelle im Schleifenzyklus zu erstellen, auf die außerhalb der Schleife nicht zugegriffen werden kann.

### Mentoring

Prüfungen für Mentoring werden manuell durchgeführt.

- Suchen Sie nach Orten, um Wissen mit dem Ziel der Ausbildung des Teams zu teilen.
- Wenn Ihr Kommentar rein pädagogisch, aber nicht kritisch für die Einhaltung der Standards ist, geben Sie an, dass es nicht obligatorisch ist, dass der Autor es löst.
- Wenn Sie etwas Schönes sehen, sagen Sie dem Entwickler, insbesondere wenn sie einen Ihrer Kommentare in einer großartigen Weise angesprochen haben. Kodex-Überprüfungen konzentrieren sich oft auf Fehler, sollten aber auch Anreize und Wertschätzung für vorbildliche Verfahren bieten. Manchmal ist es sogar noch wertvoller, einem Entwickler zu sagen, was er richtig gemacht hat, als ihm mitzuteilen, was er falsch gemacht hat.

## Automatisierung

Entwickler können Automatisierung verwenden, um die ID-Kompilierung, das Datenbankschema, die Komponentenvalidierung und die Einhaltung der Kodierungsstandards zu überprüfen:

- DI-Kompilierung: Führen Sie die folgenden CLI-Befehle aus, um zu sehen, ob der Code ohne Probleme kompiliert werden kann.

  ```bash
  bin/magento module:disable -n -q --all || exit;
  bin/magento module:enable -n -q --all || exit;
  bin/magento cache:enable -n -q || exit;
  bin/magento cache:flush -n -q || exit;
  rm -rf generated/*
  rm -rf var/view_preprocessed/*
  rm -rf pub/static/*
  rm -rf var/cache/*
  bin/magento deploy:mode:set --skip-compilation production || exit;
  bin/magento setup:di:compile -vv || exit;
  bin/magento setup:static-content:deploy en_US || exit;
  bin/magento deploy:mode:set developer || exit;
  ```

- Datenbankschema `whitelist.json`—Führen Sie den folgenden CLI-Befehl aus und überprüfen Sie, ob das `db_schema_whitelist.json` -Datei hinzugefügt oder geändert wird.

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- Composer validate - Validieren Sie die `composer.json` Datei, indem Sie den folgenden CLI-Befehl im Verzeichnis ausführen, das die `composer.json` -Datei.

  ```bash
  composer validate
  ```

- Codierungsstandard - Installieren und führen Sie das Coding Standard-Tool aus und führen Sie es mit Ihrem -Modul aus. Die folgende Datei zeigt, wie sie durch Eingabe von `mcs ./app/code/Vendor/Module/`.

  ```bash
  #!/usr/bin/env bash
  $HOME/web/magento/magento-coding-standard/vendor/bin/phpcs --standard=Magento2 "$@"
  ```

- PHP

  ```bash
  ./vendor/bin/phpstan analyze app/code/Vendor/Module
  ```

- PhpStorm-Inspektion

- PhpStorm PHP Copy/Paste Detektor
