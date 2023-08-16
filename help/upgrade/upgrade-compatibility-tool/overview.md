---
title: Übersicht über die [!DNL Upgrade Compatibility Tool]
description: Informationen zum [!DNL Upgrade Compatibility Tool] und wie es Ihnen bei Ihrem Adobe Commerce-Projekt helfen kann.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: ad7f05eaa5f144b5a8616307d65be635a0c499eb
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Guide - Übersicht

{{commerce-only}}

Dieses Handbuch richtet sich an Administratoren und Softwareingenieure von Adobe Commerce. Sie enthält detaillierte Informationen zur Installation der [!DNL Upgrade Compatibility Tool], sowie die Konfiguration und Verwaltung. Es wird von einem grundlegenden Verständnis der grundlegenden Commerce-Konfiguration und -Funktionalität ausgegangen.

## Übersicht über die [!DNL Upgrade Compatibility Tool]

Die [!DNL Upgrade Compatibility Tool] ist ein Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle Module und der darin installierte Core-Code analysiert werden. Es wird eine Liste kritischer Probleme, Fehler und Warnungen zurückgegeben, die behoben werden müssen, bevor auf eine neuere Version von Adobe Commerce aktualisiert wird.

## Verwenden Sie die [!DNL Upgrade Compatibility Tool]

Sie können die [!DNL Upgrade Compatibility Tool] über:

- Eigenständig [Befehlszeilenschnittstelle](../upgrade-compatibility-tool/run.md) -Tool. Die vollständige Liste der verfügbaren Befehle finden Sie im [`bin/uct` reference](/help/reference/uct.md).
- Integrieren der [!DNL Upgrade Compatibility Tool] mit dem [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Eine Ausführungskonfiguration innerhalb der [Magento PHPStorm-Plugin](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Workflow

Das folgende Diagramm zeigt die möglichen Workflows beim Ausführen der [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Abbildung](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] Demo

In diesem Video erfahren Sie mehr über [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Verbessern der [!DNL Upgrade Compatibility Tool]

Verwenden Sie die folgenden Ressourcen, wenn Sie Informationen benötigen oder Fragen haben, die nicht in diesem Handbuch behandelt werden:

So stellen Sie eine Verbindung zu [!DNL Upgrade Compatibility Tool] Team, kontaktieren Sie uns über den Engineering Slack Channel [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Wir möchten Ihr Feedback, Ihre Probleme und Anregungen hören, um uns bei der Verbesserung des Tools zu unterstützen.

Die [!DNL Upgrade Compatibility Tool] verwendet Regeln, die in unserer [Kodierungsstandards](https://developer.adobe.com/commerce/php/coding-standards/) , um sicherzustellen, dass Ihr Projekt die Best Practices von Adobe Commerce befolgt, und um Sie bei der Verbesserung und Erweiterung der [!DNL Upgrade Compatibility Tool].

Siehe Abschnitt [Beitragen](https://developer.adobe.com/commerce/php/coding-standards/contributing/) Thema für weitere Informationen zum Thema beitragende Kodierungsstandards.

## Ressourcen

In den folgenden Ressourcen finden Sie Informationen zu Adobe Commerce-Upgrades:

- Die [Upgrade-Handbuch](../overview.md) bietet einen Überblick über die typischen Journey und Best Practices für die Aktualisierung von Adobe Commerce oder Magento Open Source, die auf diesem Journey folgen.
- Die [Bevorstehende Versionen](https://devdocs.magento.com/release/) auf der Seite finden Sie die Daten für geplante und bevorstehende Versionen.
- Die [Community-Ressourcen](https://developer.adobe.com/commerce/contributor/community/) -Seite, um Diskussionen zu beginnen oder weitere Informationen zu finden.
- Überprüfen Sie die [verwandte Tools](../upgrade-compatibility-tool/related-tools.md) für nützliche Tools in Ihrer typischen Upgrade-Journey.
