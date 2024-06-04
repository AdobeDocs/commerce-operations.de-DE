---
title: Upgrade der Implementierung
description: Erfahren Sie mehr über die verschiedenen Phasen der Implementierung der Aktualisierung für Adobe Commerce-Projekte.
exl-id: d64855a7-73ee-463f-a314-6a8d4ebe4726
source-git-commit: a81d2c0b6526c2c8c8c5c4652c83595667985543
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 1%

---

# Upgrade der Implementierung

Die Upgrade-Implementierung besteht aus fünf Phasen:

- Upgrade-Analyse
- Entwicklung und Qualitätssicherung (QS)
- Anwenderakzeptanztests (UAT) und Vorbereitung auf den Start
- Launch
- Nach dem Start

## Upgrade-Analyse

Die Analyse ist wohl der wichtigste Teil des Aktualisierungsprozesses. Eine gut ausgeführte Analyse spart Ihnen Zeit und schränkt Überraschungen in der Zukunft ein. Das Ergebnis dieser Phase sollte eine detaillierte Upgrade-Checkliste und ein Dokument mit allen Abhängigkeiten sein.

Im Folgenden finden Sie Elemente, die Sie in eine gründliche Analyse aufnehmen möchten:

- **Umfang der Zielversion**—Dokumentation zu [Experience League](../../release/release-notes/overview.md) und Informationen aus Webinaren zur Partnerversion enthalten alle Details, die Sie über Ihr Target-Upgrade wissen müssen.

- **[!DNL Upgrade Compatibility Tool]Ergebnisse**—Dieses Tool ermöglicht eine schnellere und einfachere Aktualisierung, indem Sie Ihren aktuellen Code mit dem Code der Zielversion vergleichen und einen Bericht mit allen zu behebenden Problemen erstellen. Siehe [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md). Zu den wichtigsten Details des Berichts gehören:

   - Aktuelle installierte Version
   - Upgrade der Zielversion
   - Anzahl und Details der gefundenen kritischen Fehler

  >[!TIP]
  >
  >Alle diese Informationen (und mehr) sind im Site-weiten Analyse-Tool verfügbar. [Dashboard](../../tools/site-wide-analysis-tool/dashboard.md).

- Upgrade der Dienste zur Unterstützung der Zielversion. Verwenden Sie die folgende Tabellenvorlage, um festzulegen, welche Dienste Sie aktualisieren müssen. Verwenden Sie die [Systemanforderungen](../../installation/system-requirements.md) um zu bestimmen, was zum _Upgrade auf_ Spalte.


  | Dienst | Aktuelle Version | Upgrade auf | Hinweise |
  |-----------------|-----------------|------------|----------------------------------------------------------|
  | PHP | 7,4 | 8,1 |                                                          |
  | Redis | 6,0 | 6,2 |                                                          |
  | [!DNL RabbitMQ] | 3,8 | 3,9 | Derzeit nicht verwendet, aber wir sollten erwägen, es zu verwenden |
  | MariaDB (Cloud) | 10,4 | 10,6 |                                                          |
  | MySQL | 8,0 | -/-/ |                                                          |
  | Verfasser | 1,9,2 | 2,2 |                                                          |
  | Elasticsearch | 7,10 | 7,17 |                                                          |

- **Erweiterungen und Module von Drittanbietern**—Verwenden Sie diese Tabellenvorlage, um den Status Ihrer Erweiterungen und Anpassungen zu verstehen, sodass Sie strategische Entscheidungen treffen und Aktionen definieren können. Dies ist eine Möglichkeit, alle Erweiterungen zu ersetzen, die möglicherweise nativ in Adobe Commerce sind, um die Komplexität Ihres Projekts zu minimieren. Verwenden Sie die `bin/magento module:status` -Befehl, um eine Liste von Modulen und Erweiterungen anzuzeigen.

  | # | Erweiterung/<br>Modulname | Composer-Paket | Anbieter | Aktuelle Version | Funktionalität | Kompatibel mit der neuesten<br>Commerce-Version? | Probleme | Nativ für Commerce? | Aktion | Hinweise |
  |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
  | 1 | Name und Link der Erweiterung | extension/<br>extensionx-magento-2 | Name des Anbieters | Version installiert | Geschäftsanforderungen | Ja/Nein | Auflisten identifizierter Probleme mit dieser Erweiterung | Ja/Nein | Keep/Replace/<br>Entfernen |       |

- **Benutzerdefinierte Module**—Ähnlich wie bei der Tabelle mit Modulen von Drittanbietern hilft Ihnen diese Vorlage, den Status und die Aktionen zu verfolgen und zu verstehen, die für die Aktualisierung benutzerdefinierter Module erforderlich sind.

  | # | Modulname | Funktionalität | Erforderlich? | Nativ für Commerce? | Aktion | Hinweise |
  |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
  | 1 | Modulname | Geschäftsanforderungen | Ja/Nein | Ja/Nein | Behalten/Ersetzen/Entfernen |       |

- **Composer-Pakete und -Abhängigkeiten in Composer.json, die eine Aktualisierung erfordern.**

Darüber hinaus können Partner an [Beta-Versionen von Adobe Commerce](../../release/beta.md) und nutzen Sie Vorabversionschancen, um frühzeitig auf den Code für eine bevorstehende Version zugreifen zu können. Durch frühzeitigen Zugriff auf den Code können Entwickler sich auf ausreichend Zeit vorbereiten, um das Upgrade bis zum allgemeinen Verfügbarkeitsdatum (GA) abzuschließen. Beta-Code wird in der Regel fünf Wochen vor dem GA-Datum veröffentlicht und Vorversionen werden zwei Wochen im Voraus veröffentlicht.

## Entwicklung und Qualitätssicherung

Beim Testen handelt es sich um die Phase eines Upgrades, für die die meiste Zeit benötigt wird. Daher sollte dieser Prozess so automatisiert wie möglich sein. Die _[Handbuch zum Anwendungstest](https://developer.adobe.com/commerce/testing/guide/)_ enthält Details zur Einrichtung und Verwendung von Tools für Plattform- und Systemtests für eine schnellere Qualitätssicherung. Verwenden Sie eine Staging-Umgebung, um Ihre Aktualisierung zu testen und zu validieren, bevor Sie zur Produktion wechseln.

## UAT &amp; Vorbereitung des Launches

UAT ist eine der letzten Phasen des Upgrades, für die eine Überprüfung und Validierung der Website erforderlich ist. Sie müssen auch entscheiden, wann und ob Sie eine Wartungsseite benötigen. Planen Sie Cron-Prozesse und Drittanbieter-Nachrichten.

Da sich das Bereitstellungsdatum nähert, ist Kommunikation unerlässlich. Wenn mehr Menschen über die Veränderung am Horizont wissen, wie sie sich auf sie auswirkt und wie sie sie angehen müssen, dann ist es wahrscheinlicher, dass Sie einen erfolgreichen Start haben. Scheuen Sie sich nicht, jeden Schritt des Weges zu überkommunizieren - es erhöht die Wahrscheinlichkeit, dass Sie von allen Beteiligten, sobald Sie live gehen, helle Rezensionen erwarten!

## Launch

Führen Sie das Upgrade durch, indem Sie es in der Produktion bereitstellen und die Erweiterungen aktualisieren. Stellen Sie sicher, dass Sie kritische Pfadflüsse mit simulierten Bestellungen testen. Sehen Sie sich diese [Best Practices](../prepare/best-practices.md) für einige Tipps zum Starten mit minimalen Problemen.

Befolgen Sie Ihren Kommunikationsplan und stellen Sie sicher, dass alle Beteiligten über das Upgrade informiert und umfassend für dessen Unterstützung geschult sind.

Sprechen Sie schließlich mit Ihrem Team, um die gelernten Erfahrungen und Fallstricke zu ermitteln. Diese Retrospektive hilft Ihnen, den Prozess das nächste Mal zu verbessern.

## Nach dem Start

Überprüfen Sie nach dem Start Ihrer Site die Analysedaten, die Google-Suchkonsole und andere Ressourcen, um sicherzustellen, dass keine unerwarteten Probleme auftreten und alles erwartungsgemäß funktioniert.

Es ist immer eine gute Idee, die Leistung durch gut entwickelte Überwachungstools im Auge zu behalten. Es gibt viele Tools und Möglichkeiten, die Leistung Ihrer Site zu überwachen. Wählen Sie daher unbedingt eines aus, das sich gut mit Ihrer Organisation verbindet. Wir empfehlen Adobe Commerce-Kunden, die unser Cloud-Infrastrukturverwaltungssystem verwenden, die Vorteile von Diensten wie [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html) zur Überwachung der Site-Leistung.
