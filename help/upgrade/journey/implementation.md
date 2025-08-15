---
title: Upgrade-Implementierung
description: Erfahren Sie mehr über die verschiedenen Phasen der Upgrade-Implementierung für Adobe Commerce-Projekte.
exl-id: d64855a7-73ee-463f-a314-6a8d4ebe4726
source-git-commit: a81d2c0b6526c2c8c8c5c4652c83595667985543
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 1%

---

# Upgrade-Implementierung

Die Upgrade-Implementierung umfasst fünf Phasen:

- Analyse aktualisieren
- Entwicklung und Qualitätssicherung (QA)
- Benutzerakzeptanztests (UAT) und Vorbereitung auf den Launch
- Starten
- Nach der Markteinführung

## Analyse aktualisieren

Analyse ist der wohl wichtigste Teil des Upgrade-Prozesses. Eine gut durchgeführte Analyse spart Ihnen Zeit und begrenzt Überraschungen in der Zukunft. Das Ergebnis dieser Phase sollte eine detaillierte Upgrade-Checkliste und ein Dokument mit allen Abhängigkeiten sein.

Im Folgenden finden Sie Elemente, die Sie in eine gründliche Analyse einbeziehen sollten:

- **Umfang der Target-Version** - Die Dokumentation zu [Experience League](../../release/release-notes/overview.md) und Informationen aus Partner-Release-Webinaren bieten alle Details, die Sie über Ihr Target-Upgrade wissen müssen.

- **[!DNL Upgrade Compatibility Tool]Ergebnisse**: Dieses Tool macht jedes Upgrade schneller und einfacher, indem Ihr aktueller Code mit dem Code der Zielversion verglichen wird und ein Bericht über alle Probleme erstellt wird, die behoben werden müssen. Siehe die [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md). Zu den wichtigsten Details des Berichts gehören:

   - Aktuelle installierte Version
   - Zielversion aktualisieren
   - Anzahl und Details der gefundenen kritischen Fehler

  >[!TIP]
  >
  >All diese Informationen (und mehr) sind im Dashboard des Site-Wide Analysis Tool [](../../tools/site-wide-analysis-tool/dashboard.md) verfügbar.

- Aktualisieren von Diensten zur Unterstützung der Zielversion. Verwenden Sie die folgende Tabellenvorlage, um festzustellen, welche Services Sie aktualisieren müssen. Verwenden Sie die [Systemanforderungen](../../installation/system-requirements.md) um zu bestimmen, was zur Spalte _Upgrade auf“ hinzugefügt_ soll.


  | Service | Aktuelle Version | Aktualisieren auf | Notizen |
  |-----------------|-----------------|------------|----------------------------------------------------------|
  | PHP | 7,4 | 8,1 |                                                          |
  | Redis | 6,0 | 6,2 |                                                          |
  | [!DNL RabbitMQ] | 3,8 | 3,9 | Wird derzeit nicht verwendet, aber wir sollten erwägen, es zu verwenden |
  | MariaDB (Cloud) | 10,4 | 10,6 |                                                          |
  | MySQL | 8,0 | -/-/ |                                                          |
  | Komponist | 1,9,2 | 2,2 |                                                          |
  | Elasticsearch | 7,10 | 7,17 |                                                          |

- **Erweiterungen und Drittanbietermodule** - Verwenden Sie diese Tabellenvorlage, um den Status Ihrer Erweiterungen und Anpassungen zu verstehen, damit Sie strategische Entscheidungen treffen und Aktionen definieren können. Dies ist eine Möglichkeit, alle Erweiterungen zu ersetzen, die in Adobe Commerce nativ sein könnten, um die Komplexität Ihres Projekts zu minimieren. Verwenden Sie den Befehl `bin/magento module:status` , um eine Liste der Module und Erweiterungen anzuzeigen.

  | # | Name <br> Erweiterung/Moduls | Komponentenpaket | Anbieter | Aktuelle Version | Funktionalität | Mit der neuesten <br>Commerce-Version kompatibel? | Probleme | Nativ in Commerce? | Aktion | Notizen |
  |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
  | 1 | Name und Link der Erweiterung | extension/<br>extensionX-magento-2 | Anbietername | Installierte Version | Geschäftsanforderungen | Ja/Nein | Auflisten der identifizierten Probleme, die mit dieser Erweiterung auftreten können | Ja/Nein | Keep/Replace/<br>Remove |       |

- **Benutzerdefinierte Module** - Ähnlich wie die Tabelle mit Drittanbietermodulen hilft Ihnen diese Vorlage, den Status und die Aktionen zu verfolgen und zu verstehen, die zum Aktualisieren benutzerdefinierter Module erforderlich sind.

  | # | Modulname | Funktionalität | Erforderlich? | Nativ in Commerce? | Aktion | Notizen |
  |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
  | 1 | Modulname | Geschäftsanforderungen | Ja/Nein | Ja/Nein | Behalten/Ersetzen/Entfernen |       |

- **Composer-Pakete und -Abhängigkeiten in „composer.json“, die eine Aktualisierung erfordern.**

Darüber hinaus können Partner an [Adobe Commerce-Betaversionen teilnehmen ](../../release/beta.md) Vorabversionschancen nutzen, um frühzeitig Zugriff auf den Code einer kommenden Version zu erhalten. Wenn Entwickler frühzeitig Zugriff auf den Code erhalten, haben sie genügend Zeit, um das Upgrade bis zum allgemeinen Verfügbarkeitsdatum abzuschließen. Beta-Code wird in der Regel fünf Wochen vor dem GA-Datum veröffentlicht und Vorabversionen zwei Wochen im Voraus.

## Entwicklung und Qualitätssicherung

Beim Testen handelt es sich um die Phase eines Upgrades, die die meiste Zeit in Anspruch nimmt. Daher sollte dieser Prozess so weit wie möglich automatisiert werden. Das _[Handbuch zu Anwendungstests](https://developer.adobe.com/commerce/testing/guide/)_ enthält Details zum Einrichten und Verwenden von Plattform- und Systemtest-Tools für eine schnellere Qualitätssicherung. Verwenden Sie eine Staging-Umgebung, um Ihr Upgrade zu testen und zu validieren, bevor Sie zur Produktion wechseln.

## UAT und Vorbereitung auf den Launch

UAT ist eine der letzten Phasen des Upgrades, für die die Site überprüft und validiert werden muss. Sie müssen auch entscheiden, wann Sie bereitstellen und ob Sie eine Wartungsseite benötigen. Planen Sie Cron-Prozesse und Nachrichten von Drittanbietern.

Da das Datum der Einführung näher rückt, ist Kommunikation unerlässlich. Wenn mehr Menschen über die Veränderungen am Horizont Bescheid wissen, wie sie sich auf sie auswirken und wie sie damit umgehen müssen, dann ist ein erfolgreicher Launch wahrscheinlicher. Scheuen Sie sich nicht, jeden Schritt des Weges zu übermäßig zu kommunizieren - es erhöht die Wahrscheinlichkeit von begeisternden Rezensionen von allen Beteiligten, sobald Sie live gehen!

## Starten

Schließen Sie das Upgrade ab, indem Sie Erweiterungen für die Produktion bereitstellen und aktualisieren. Stellen Sie sicher, dass Sie kritische Pfadflüsse mit simulierten Bestellungen testen. Sehen Sie sich diese [Best Practices“ an](../prepare/best-practices.md) um einige Tipps zum Starten mit minimalen Problemen zu erhalten.

Befolgen Sie Ihren Kommunikationsplan und stellen Sie sicher, dass alle Beteiligten über das Upgrade informiert und entsprechend geschult sind.

Besprechen Sie abschließend mit Ihrem Team die gewonnenen Erkenntnisse und Fallstricke. Diese Retrospektive hilft Ihnen, den Prozess beim nächsten Mal zu verbessern.

## Nach dem Launch

Überprüfen Sie nach dem Start Ihrer Site Ihre Analysedaten, die Google-Suchkonsole und andere Ressourcen, um sicherzustellen, dass es keine unerwarteten Probleme gibt und alles erwartungsgemäß funktioniert.

Es ist immer empfehlenswert, die Leistung mit gut konzipierten Überwachungs-Tools im Auge zu behalten. Es gibt viele Tools und Möglichkeiten, die Leistung Ihrer Site zu überwachen. Achten Sie daher darauf, eines auszuwählen, das gut zu Ihrer Organisation passt. Wir empfehlen, dass Adobe Commerce-Kunden, die unser Cloud-Infrastrukturverwaltungssystem verwenden, Services wie [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html) zur Überwachung der Site-Leistung nutzen.
