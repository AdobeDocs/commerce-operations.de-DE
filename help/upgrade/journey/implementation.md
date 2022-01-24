---
title: Upgrade der Implementierung
description: Erfahren Sie mehr über die verschiedenen Phasen der Implementierung von Upgrades für Adobe Commerce- und Magento Open Source-Projekte.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 1%

---


# Upgrade der Implementierung

Die Upgrade-Implementierung besteht aus fünf Phasen:

- Upgrade-Analyse
- Entwicklung und Qualitätssicherung (QA)
- Anwenderakzeptanztests (UAT) und Vorbereitung auf den Start
- Launch
- Nach dem Start

## Upgrade-Analyse

Die Analyse ist wohl der wichtigste Teil des Aktualisierungsprozesses. Eine gut ausgeführte Analyse spart Ihnen Zeit und schränkt Überraschungen in der Zukunft ein. Das Ergebnis dieser Phase sollte eine detaillierte Upgrade-Checkliste und ein Dokument mit allen Abhängigkeiten sein.

Im Folgenden finden Sie Elemente, die Sie in eine gründliche Analyse aufnehmen möchten:

- **Umfang der Zielversion**—Dokumentation zu [Commerce DevDocs](https://devdocs.magento.com) und Informationen aus Webinaren zur Partnerversion enthalten alle Details, die Sie über Ihr Target-Upgrade wissen müssen.

- **Ergebnisse des Upgrade-Kompatibilitätstools**—Dieses Tool ermöglicht eine schnellere und einfachere Aktualisierung, indem Sie Ihren aktuellen Code mit dem Code der Zielversion vergleichen und einen Bericht mit allen zu behebenden Problemen erstellen. Siehe [Upgrade-Kompatibilitätstool](../upgrade-compatibility-tool/overview.md). Zu den wichtigsten Details des Berichts gehören:

   - Aktuelle installierte Version
   - Upgrade der Zielversion
   - Anzahl und Details der festgestellten kritischen Fehler

- Upgrade der Dienste zur Unterstützung der Zielversion. Verwenden Sie die folgende Tabellenvorlage, um festzulegen, welche Dienste Sie aktualisieren müssen. Verwenden Sie die [Systemanforderungen](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) um zu bestimmen, was zum _Upgrade auf_ Spalte.


   | Diensleistung | Aktuelle Version | Upgrade auf | Hinweise |
   |-----------------|-----------------|------------|----------------------------------------------------------|
   | PHP | 7,2,33 | 8,1 |  |
   | Redis | 5,05 | 6,0 |  |
   | RabbitMQ | 3,7 | 3,8 | Derzeit nicht verwendet, aber wir sollten erwägen, es zu verwenden |
   | MariaDB (Cloud) | 10.2.33 | Artikel 10 Absatz 4 |  |
   | MySQL | 8,0 |  |  |
   | Verfasser | 1,9,2 | 2,0 |  |
   | Elasticsearch | 7,7 | 7,10 |  |

- **Erweiterungen und Module von Drittanbietern**—Verwenden Sie diese Tabellenvorlage, um den Status Ihrer Erweiterungen und Anpassungen zu verstehen, sodass Sie strategische Entscheidungen treffen und Aktionen definieren können. Dies bietet die Möglichkeit, alle Erweiterungen zu ersetzen, die möglicherweise nativ für Adobe Commerce oder Magento Open Source sind, um die Komplexität Ihres Projekts zu minimieren. Verwenden Sie die `bin/magento module:status` -Befehl, um eine Liste von Modulen und Erweiterungen anzuzeigen.

   | # | Erweiterung/<br>Modulname | Composer-Paket | Anbieter | Aktuelle Version | Funktionalität | Kompatibel mit der neuesten<br>Commerce-Version? | Probleme | Nativ für Commerce? | Aktion | Hinweise |
   |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
   | 1 | Name und Link der Erweiterung | extension/<br>extensionx-magento-2 | Name des Anbieters | Version installiert | Geschäftsanforderungen | Ja/Nein | Auflisten identifizierter Probleme mit dieser Erweiterung | Ja/Nein | Keep/Replace/<br>Entfernen |  |

- **Benutzerdefinierte Module**—Ähnlich wie bei der Tabelle mit Modulen von Drittanbietern hilft Ihnen diese Vorlage, den Status und die Aktionen zu verfolgen und zu verstehen, die für die Aktualisierung benutzerdefinierter Module erforderlich sind.

   | # | Modulname | Funktionalität | Erforderlich? | Nativ für Commerce? | Aktion | Hinweise |
   |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
   | 1 | Modulname | Geschäftsanforderungen | Ja/Nein | Ja/Nein | Behalten/Ersetzen/Entfernen |  |

- **Composer-Pakete und -Abhängigkeiten in Composer.json, die eine Aktualisierung erfordern.**

Darüber hinaus können Partner an der [Adobe Commerce Beta-Programm](https://devdocs.magento.com/release/beta-program.html) und nutzen Sie Vorabversionschancen, um frühzeitig auf den Code für eine bevorstehende Version zugreifen zu können. Durch frühzeitigen Zugriff auf den Code können Entwickler sich auf ausreichend Zeit vorbereiten, um das Upgrade bis zum allgemeinen Verfügbarkeitsdatum (GA) abzuschließen. Beta-Code wird in der Regel fünf Wochen vor dem GA-Datum veröffentlicht und Vorversionen werden zwei Wochen im Voraus veröffentlicht. Für Version 2.4.4 begann Adobe fünf Monate vor dem GA-Datum (8. März 2022) mit der Veröffentlichung des Beta-Codes. Partner können nun mit der Vorbereitung auf dieses Upgrade beginnen, indem sie [Anmeldung für das Programm](https://community.magento.com/t5/Magento-DevBlog/BREAKING-NEWS-2-4-4-beta-releases-are-coming-soon/ba-p/484310).

## Entwicklung und Qualitätssicherung

Beim Testen handelt es sich um die Phase eines Upgrades, für die die meiste Zeit benötigt wird. Daher sollte dieser Prozess so automatisiert wie möglich sein. Die _[Handbuch zum Anwendungstest](https://devdocs.magento.com/guides/v2.4/test/testing.html)_ enthält Details zur Einrichtung und Verwendung von Tools für Plattform- und Systemtests für eine schnellere Qualitätssicherung. Verwenden Sie eine Staging-Umgebung, um Ihre Aktualisierung zu testen und zu validieren, bevor Sie zur Produktion wechseln.

## UAT &amp; Vorbereitung des Launches

UAT ist eine der letzten Phasen des Upgrades, für die eine Überprüfung und Validierung der Website erforderlich ist. Sie müssen auch entscheiden, wann und ob Sie eine Wartungsseite benötigen. Planen Sie Cron-Prozesse und Drittanbieter-Nachrichten.

Da sich das Bereitstellungsdatum nähert, ist Kommunikation unerlässlich. Wenn mehr Menschen über die Veränderung am Horizont wissen, wie sie sich auf sie auswirkt und wie sie sie angehen müssen, dann ist es wahrscheinlicher, dass Sie einen erfolgreichen Start haben. Scheuen Sie sich nicht, jeden Schritt des Weges zu überkommunizieren - es erhöht die Wahrscheinlichkeit, dass Sie von allen Beteiligten, sobald Sie live gehen, helle Rezensionen erwarten!

## Launch

Führen Sie das Upgrade durch, indem Sie es in der Produktion bereitstellen und die Erweiterungen aktualisieren. Stellen Sie sicher, dass Sie kritische Pfadflüsse mit simulierten Bestellungen testen. Sehen Sie sich diese an [Best Practices](../prepare/best-practices.md) für einige Tipps zum Starten mit minimalen Problemen.

Befolgen Sie Ihren Kommunikationsplan und stellen Sie sicher, dass alle Beteiligten über das Upgrade informiert und umfassend für dessen Unterstützung geschult sind.

Sprechen Sie schließlich mit Ihrem Team, um die gelernten Erfahrungen und Fallstricke zu ermitteln. Diese Retrospektive hilft Ihnen, den Prozess das nächste Mal zu verbessern.

## Nach dem Start

Überprüfen Sie nach dem Start Ihrer Site die Analysedaten, die Google-Suchkonsole und andere Ressourcen, um sicherzustellen, dass keine unerwarteten Probleme auftreten und alles erwartungsgemäß funktioniert.

Es ist immer eine gute Idee, die Leistung durch gut entwickelte Überwachungstools im Auge zu behalten. Es gibt viele Tools und Möglichkeiten, die Leistung Ihrer Site zu überwachen. Wählen Sie daher unbedingt eines aus, das sich gut mit Ihrer Organisation verbindet. Wir empfehlen Adobe Commerce-Kunden, die unser Cloud-Infrastrukturverwaltungssystem verwenden, die Vorteile von Diensten wie [Neuer Relikt](https://devdocs.magento.com/cloud/project/new-relic.html) zur Überwachung der Site-Leistung.