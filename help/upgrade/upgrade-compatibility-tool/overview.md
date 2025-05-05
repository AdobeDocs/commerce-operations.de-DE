---
title: Überblick über die [!DNL Upgrade Compatibility Tool]
description: Erfahren Sie mehr über  [!DNL Upgrade Compatibility Tool]  und wie Sie damit Ihr Adobe Commerce-Projekt unterstützen können.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Handbuch - Übersicht

{{commerce-only}}

Dieses Handbuch richtet sich an Administratoren und Software-Ingenieure von Adobe Commerce. Es enthält detaillierte Informationen über die Installation des [!DNL Upgrade Compatibility Tool] sowie dessen Konfiguration und Verwaltung. Es setzt ein grundlegendes Verständnis der Commerce-Kernkonfiguration und -funktionen voraus.

## Überblick über die [!DNL Upgrade Compatibility Tool]

Der [!DNL Upgrade Compatibility Tool] ist ein Tool, das eine benutzerdefinierte Adobe Commerce-Instanz mit einer bestimmten Version vergleicht, indem alle darin installierten Module und der Kern-Code analysiert werden. Sie gibt eine Liste kritischer Probleme, Fehler und Warnungen zurück, die vor einem Upgrade auf eine neuere Version von Adobe Commerce behoben werden müssen.

## [!DNL Upgrade Compatibility Tool] verwenden

Sie können die [!DNL Upgrade Compatibility Tool] wie folgt verwenden:

- Als eigenständiges [Befehlszeilenschnittstelle](../upgrade-compatibility-tool/run.md)-Tool. Eine vollständige Liste der verfügbaren Befehle finden Sie in der [`bin/uct`-Referenz](../../tools/reference/uct.md).
- Integrieren des [!DNL Upgrade Compatibility Tool] mit dem [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Eine Ausführungskonfiguration innerhalb des [Magento-PHPStorm-Plug-ins](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Workflow

Das folgende Diagramm zeigt die möglichen Workflows beim Ausführen der [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagramm](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] Demo

In diesem Video erfahren Sie mehr über die [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/3409509?quality=12&captions=ger)

## Helfen Sie, die [!DNL Upgrade Compatibility Tool] zu verbessern

Wenn Sie Informationen benötigen oder Fragen haben, die in diesem Handbuch nicht behandelt werden, verwenden Sie die folgenden Ressourcen:

Um eine Verbindung zum [!DNL Upgrade Compatibility Tool]-Team herzustellen, kontaktieren Sie uns auf dem Engineering-Slack-Kanal [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Wir möchten Ihr Feedback, Ihre Probleme und Vorschläge hören, um das Tool zu verbessern.

Der [!DNL Upgrade Compatibility Tool] verwendet Regeln, die in unseren [Codierungsstandards](https://developer.adobe.com/commerce/php/coding-standards/) definiert sind, um sicherzustellen, dass Ihr Projekt den Best Practices von Adobe Commerce entspricht, und um Sie bei der Verbesserung und Erweiterung der [!DNL Upgrade Compatibility Tool] zu unterstützen.

Weitere Informationen zu beitragenden Kodierungsstandards finden [&#128279;](https://developer.adobe.com/commerce/php/coding-standards/contributing/) unter Contribute.

## Ressourcen

In den folgenden Ressourcen finden Sie Informationen zu Adobe Commerce-Upgrades:

- Das [Upgrade-Handbuch](../overview.md) bietet einen Überblick über die typische Adobe Commerce-Upgrade-Journey und Best Practices, die auf dieser Journey befolgt werden sollten.
- Die [bevorstehende Versionen](https://experienceleague.adobe.com/de/docs/commerce-operations/release/planning/schedule) enthält die Daten für geplante und bevorstehende Versionen.
- Die [Community-Ressourcen](https://developer.adobe.com/commerce/contributor/community/)-Seite ist der Ort, um Diskussionen zu beginnen oder mehr Informationen zu finden.
- Auf der Seite [Verwandte Tools](../upgrade-compatibility-tool/related-tools.md) finden Sie hilfreiche Tools auf Ihrer typischen Upgrade-Journey.
