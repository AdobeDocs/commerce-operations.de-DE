---
title: Best Practices für die Code-Überprüfung
description: Erfahren Sie mehr über Best Practices zur Überprüfung von Code für die Entwicklungsphase von Adobe Commerce-Projekten.
feature: Best Practices
role: Developer
exl-id: 1ef78bce-2e69-4c95-a26e-1bf7196ce546
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 0%

---

# Best Practices für die Überprüfung des Codes für Adobe Commerce

Das Hauptziel der Code-Überprüfung besteht darin zu überprüfen, ob die implementierte Funktionalität die Anforderungen aus Leistungs-, Architektur- und Sicherheitssicht optimal erfüllt.

Außerdem soll durch die Code-Überprüfung sichergestellt werden, dass der Code den Best Practices für die Adobe Commerce-Entwicklung entspricht, leicht zu verstehen und zu pflegen ist und den Codierungsstandards entspricht. Die meisten Codierungsstandards sollten automatisch von entsprechenden Tools überprüft werden.

## Empfohlener Code-Überprüfungsprozess

Im Großen und Ganzen sollte der Code-Überprüfungsprozess die folgenden Schritte umfassen:

1. Checkout-Funktionsverzweigung in der lokalen Entwicklungsumgebung.
1. Wenn es eine Weile her ist, seit der Code zur Überprüfung übermittelt wurde, führen Sie die neuesten Änderungen aus der Zielverzweigung (normalerweise die QA-Verzweigung) zusammen und übertragen Sie Aktualisierungen auf die Remote-Funktionsverzweigung (falls vorhanden).
1. Führen Sie eine allgemeine Überprüfung durch, um zu überprüfen, ob der Code alle Anforderungen implementiert. Wenn es größere Diskrepanzen gibt, wenden Sie sich zur Klärung an den Entwickler.
1. Das Ausführen des Codes ist optional, aber wenn Sie Zweifel haben, dass der Code erwartungsgemäß funktioniert, oder wenn er die Effizienz des Prozesses erleichtert, testen Sie, ob die implementierte Funktionalität für die wichtigsten Nutzungsszenarien wie erwartet funktioniert. Wenn es größere Probleme gibt, beenden Sie den Überprüfungsprozess und öffnen Sie das Ticket erneut mit entsprechenden Kommentaren.
1. Führen Sie eine gründliche Überprüfung durch, um zu überprüfen, ob der Code alle Anforderungen implementiert. Wenn Probleme auftreten, fügen Sie der Pull-Anfrage entsprechende Kommentare hinzu und öffnen Sie das Ticket erneut.
1. Wenn alles gut aussieht, führen Sie die Pull-Anfrage zusammen (oder übergeben Sie sie an die nächste Code-Prüfungsebene, falls eine eingerichtet wurde).

Beachten Sie außerdem die folgenden Punkte bei der Implementierung von Code-Überprüfungsprozessen:

- Die Code-Überprüfung ist ein primäres Tool für die Kommunikation und den Wissenstransfer innerhalb eines Teams. Selbst wenn eine Pull-Anfrage keine größeren Probleme enthält und die erforderliche Geschäftslogik implementiert, können Sie sie als Gelegenheit nutzen, nach der Zusammenführung weitere Verbesserungen vorzuschlagen.

- Im Durchschnitt sollte die Überprüfung von Code nicht mehr als 10 % bis 20 % des Entwicklungsaufwands in Anspruch nehmen. Das setzt voraus, dass das Entwicklungsteam aus erfahrenen Ingenieuren besteht, die gut zusammenarbeiten. Wenn die Überprüfung des Codes länger dauert, kann dies das Projektbudget und den Zeitrahmen beeinflussen.

- Beheben Sie Probleme mit übermäßigem Aufwand für Code-Überprüfungen, indem Sie die Grundursache identifizieren. Normalerweise liegt es daran, dass entweder Anforderungen schlecht in Entwicklungs-Tickets übersetzt werden (aufgrund von Kommunikationsproblemen, schlechten Benutzergeschichten) oder es sich um ein Coaching-Problem handelt. Im ersten Fall wird als Risikominderung empfohlen, sicherzustellen, dass die Tickets über genügend Informationen verfügen, damit die Team-Mitglieder die Anforderungen effizient erfüllen können. Im zweiten Fall müssen Sie möglicherweise die Team-Struktur anpassen, um mehr erfahrene Ingenieure einzubeziehen oder eine Genehmigung außerhalb von Mentoring und Coaching zu erhalten.

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Worauf bei der Code-Überprüfung geachtet werden muss

### Stil

Der Stil kann automatisch durch Ausführen der PhpStorm-Inspektion getestet werden (siehe unten).

Stellen Sie sicher, [PHPMD und PHPCS](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) zu konfigurieren und das [Coding Standard](https://github.com/magento/magento-coding-standard)-Tool über die CLI (auch unten) auszuführen. Es gibt einige Überschneidungen, aber beide verfügen auch über eindeutige Tests.

### Konvention und Struktur

Die Überprüfungen der Konvention und Struktur werden manuell durchgeführt.

- Ist die Klassenfunktionalität auf eine einzige Verantwortung beschränkt?
- Ist die Verzeichnisstruktur sinnvoll?
- Wird auf der richtigen Ebene ausgeführt (Server, Client, CSS, JS, Datenbank, Framework, Infrastruktur).
- Ist die Versionierung korrekt?
- Sieht der Code unkonventionell aus oder ist er so, als ob er versucht, ein Problem auf die falsche Weise zu umgehen?
- Wird die Namenskonvention für den Modul-, Paket- und Repository-Namen korrekt angewendet?
- Stellen Sie sicher, dass globale CSS-Stile sorgfältig angewendet und nicht überbeansprucht werden.

### Vollständigkeit

Die Überprüfung auf Vollständigkeit erfolgt manuell.

- Kann der Code durch Konfiguration aktiviert oder deaktiviert werden und verhält sich der gesamte erforderliche Code erwartungsgemäß?
- Sind alle Konfigurationen vorhanden, die im Ticket erwähnt werden? Überprüfen Sie Umfang, Datentyp, Validierung, Übersetzung und Standardwerte.
- Wird die Konfiguration immer auf der niedrigstmöglichen Ebene abgerufen (Store-Ansichtsebene, Website-Ebene oder globale Ebene)? Der Konfigurationsabruf muss mit der Definition des Umfangs in der `system.xml` übereinstimmen.
- Werden alle Pfade im Flussdiagramm der technischen Spezifikation abgedeckt? Werden alle anderen technischen Spezifikationen berücksichtigt?
- Sind für die neue Funktion ACLs definiert?
- Sind PHP-Dokumente klar? Sind Commit-Nachrichten klar?
- Ist irgendein Code auskommentiert oder wird Debug-Code angezeigt?

### Leistung

Die Überprüfung der Leistung erfolgt manuell, was im Zweifelsfall durch die Ausführung von Code unterstützt werden kann.

- Werden Abfragen in einer Schleife ausgeführt? Diese Schleife kann sich außerhalb der bearbeiteten Dateien befinden.
- Können Sie `cachable="false"` Attribute erkennen? Werden sie korrekt angewandt?

### Sicherheit

Die Überprüfung auf Sicherheit erfolgt manuell, was durch die Textsuche unterstützt werden kann. Ein Teil der Sicherheitsprüfung wird durch automatisierte Tests durchgeführt.

- Werden bei Bedarf Ausnahmen protokolliert? Werden die richtigen Ausnahmetypen verwendet?
- Können `around` Plug-ins vermieden werden?
- Gibt das Plug-in die richtigen Datentypen zurück?
- Können Sie Rohdaten-SQL-Abfragen finden, die mit der Datenbankabstraktionsebene erstellt werden sollen?
- Wird ein neuer Datentyp einem beliebigen Benutzer, Administrator oder Frontend bereitgestellt? Ist diese Anfälligkeit ein Sicherheitsrisiko?
- Werden benutzergenerierte Daten validiert? Alles, was vom Browser kommt, wird als benutzergeneriert betrachtet, einschließlich Cookie-Werte und Server-Kopfzeilen.

### Datenschutz und DSGVO

Die Überprüfungen für Datenschutz und [DSGVO](../../../security-and-compliance/privacy/gdpr.md) werden manuell durchgeführt.

- Verarbeitet der Code Kundendaten oder E-Mails? Achten Sie besonders darauf.
- Wenn dieser Code in einer Schleife ausgeführt werden kann, kann er dann Kundendaten von einem Schleifenzyklus zum anderen durchsickern lassen?
- Risikoindikatoren sind Importe, Cron-Aufträge, Transaktions-E-Mails und Batch-Warteschlangen-Handler.
- Sicherstellen, dass Benutzerdaten in Schleifen isoliert werden. Adobe empfiehlt die Verwendung von Factories oder Repositorys zum Erstellen von Modellen im Schleifenzyklus, auf die außerhalb der Schleife nicht zugegriffen werden kann.

### Mentoring

Die Bewertungen für das Mentoring werden manuell durchgeführt.

- Suchen Sie nach Orten, an denen Sie Wissen mit dem Ziel der Ausbildung des Teams teilen können.
- Wenn Ihr Kommentar rein informativ, aber nicht wichtig für die Einhaltung der Standards ist, geben Sie an, dass es für den Autor nicht obligatorisch ist, ihn zu lösen.
- Wenn Sie etwas Schönes sehen, sagen Sie dem Entwickler, vor allem, wenn er einen Ihrer Kommentare in einer tollen Weise angesprochen. Die Code-Überprüfungen konzentrieren sich oft auf Fehler, sollten aber auch Anreize und Anerkennung für bewährte Verfahren bieten. Manchmal ist es sogar noch wertvoller, im Hinblick auf Anleitung, einem Entwickler zu erzählen, was er richtig gemacht hat, als ihm zu erzählen, was er falsch gemacht hat.

## Automatisierung

Entwicklerinnen und Entwickler können die Automatisierung verwenden, um die ID-Kompilierung, das Datenbankschema, die Composer-Validierung und die Einhaltung der Codierungsstandards zu überprüfen:

- ID-Kompilierung - Führen Sie die folgenden CLI-Befehle aus, um zu sehen, ob der Code ohne Probleme kompiliert werden kann.

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

- Datenbankschema `whitelist.json` - Führen Sie den folgenden CLI-Befehl aus und überprüfen Sie, ob die `db_schema_whitelist.json` Datei hinzugefügt oder geändert wird.

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- Composer validate - Validieren Sie die `composer.json`-Datei, indem Sie den folgenden CLI-Befehl in dem Verzeichnis ausführen, das die `composer.json`-Datei enthält.

  ```bash
  composer validate
  ```

- Coding Standard - Installieren und führen Sie das Coding Standard-Tool aus und führen Sie es für Ihr Modul aus. Die folgende Datei zeigt, wie Sie sie aktivieren, um sie überall auszuführen, indem Sie `mcs ./app/code/Vendor/Module/` eingeben.

  ```bash
  #!/usr/bin/env bash
  $HOME/web/magento/magento-coding-standard/vendor/bin/phpcs --standard=Magento2 "$@"
  ```

- Schwebstoff

  ```bash
  ./vendor/bin/phpstan analyze app/code/Vendor/Module
  ```

- PhpStorm-Inspektion

- PhpStorm PHP Kopier-/Einfügedetektor
