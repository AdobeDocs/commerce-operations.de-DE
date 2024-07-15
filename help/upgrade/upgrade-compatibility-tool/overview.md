---
title: Überblick über den  [!DNL Upgrade Compatibility Tool]
description: Erfahren Sie mehr über den [!DNL Upgrade Compatibility Tool] und wie er Ihnen bei Ihrem Adobe Commerce-Projekt helfen kann.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: fc1be3362863d3b0fa3468380fe62ca698abac43
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Guide - Übersicht

{{commerce-only}}

Dieses Handbuch richtet sich an Administratoren und Softwareingenieure von Adobe Commerce. Es enthält detaillierte Informationen zur Installation des [!DNL Upgrade Compatibility Tool] sowie zur Konfiguration und Verwaltung. Es wird von einem grundlegenden Verständnis der grundlegenden Commerce-Konfiguration und -Funktionalität ausgegangen.

## Überblick über die [!DNL Upgrade Compatibility Tool]

Der [!DNL Upgrade Compatibility Tool] ist ein Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle darin installierten Module und der darin installierte Core-Code analysiert werden. Es wird eine Liste kritischer Probleme, Fehler und Warnungen zurückgegeben, die behoben werden müssen, bevor auf eine neuere Version von Adobe Commerce aktualisiert wird.

## Verwenden Sie den [!DNL Upgrade Compatibility Tool]

Sie können den [!DNL Upgrade Compatibility Tool] über Folgendes verwenden:

- Als eigenständiges [Befehlszeilenschnittstelle](../upgrade-compatibility-tool/run.md)-Tool. Die vollständige Liste der verfügbaren Befehle finden Sie in der [`bin/uct` Referenz](../../tools/reference/uct.md).
- Integrieren der [!DNL Upgrade Compatibility Tool] in die [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Eine Ausführungskonfiguration im [Magento PHPStorm-Plugin](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Workflow

Das folgende Diagramm zeigt die möglichen Workflows beim Ausführen von [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagramm](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] Demo

Sehen Sie sich dieses Video an, um mehr über die [!DNL Upgrade Compatibility Tool] zu erfahren:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Verbessern der [!DNL Upgrade Compatibility Tool]

Verwenden Sie die folgenden Ressourcen, wenn Sie Informationen benötigen oder Fragen haben, die nicht in diesem Handbuch behandelt werden:

Um eine Verbindung zum [!DNL Upgrade Compatibility Tool]-Team herzustellen, kontaktieren Sie uns auf dem Engineering Slack Channel [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Wir möchten Ihr Feedback, Ihre Probleme und Anregungen hören, um uns bei der Verbesserung des Tools zu unterstützen.

Der [!DNL Upgrade Compatibility Tool] verwendet Regeln, die in unseren [Kodierungsstandards](https://developer.adobe.com/commerce/php/coding-standards/) definiert sind, um sicherzustellen, dass Ihr Projekt die Best Practices von Adobe Commerce befolgt, und um Sie bei der Verbesserung und Erweiterung des [!DNL Upgrade Compatibility Tool] zu unterstützen.

Weitere Informationen zum Beitrag zu Kodierungsstandards finden Sie im Thema [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) .

## Ressourcen

In den folgenden Ressourcen finden Sie Informationen zu Adobe Commerce-Upgrades:

- Das [Upgrade-Handbuch](../overview.md) bietet einen Überblick über die typischen Journey und Best Practices für die Adobe Commerce-Aktualisierung, die auf dieser Journey folgen.
- Auf der Seite [Bevorstehende Versionen](https://devdocs.magento.com/release/) finden Sie die Daten für geplante und bevorstehende Versionen.
- Auf der Seite [Community-Ressourcen](https://developer.adobe.com/commerce/contributor/community/) können Sie Diskussionen starten oder weitere Informationen finden.
- Auf der Seite [zugehörige Tools](../upgrade-compatibility-tool/related-tools.md) finden Sie nützliche Tools in Ihrer typischen Upgrade-Journey.
