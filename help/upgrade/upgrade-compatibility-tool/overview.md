---
title: Übersicht über die [!DNL Upgrade Compatibility Tool]
description: Erfahren Sie mehr über die [!DNL Upgrade Compatibility Tool] und wie es Ihnen bei Ihrem Adobe Commerce-Projekt helfen kann.
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Guide - Übersicht

Dieses Handbuch richtet sich an Administratoren und Softwareingenieure von Adobe Commerce. Sie enthält detaillierte Informationen zur Installation der [!DNL Upgrade Compatibility Tool], sowie die Konfiguration und Verwaltung. Es wird von einem grundlegenden Verständnis der Commerce-Konfiguration und -Funktionalität ausgegangen.

## Übersicht über die [!DNL Upgrade Compatibility Tool]

{{commerce-only}

Die [!DNL Upgrade Compatibility Tool] ist ein Befehlszeilen-Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version überprüft, indem alle Module und der darin installierte Core-Code analysiert werden. Es wird eine Liste kritischer Probleme, Fehler und Warnungen zurückgegeben, die behoben werden müssen, bevor auf eine neuere Version von Adobe Commerce aktualisiert wird.

Siehe [Tool ausführen](../upgrade-compatibility-tool/run.md) für weitere Informationen.

Siehe [Installieren](../upgrade-compatibility-tool/install.md) für die ersten Schritte mit der [!DNL Upgrade Compatibility Tool].

Siehe dies [Video-Tutorial](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) , um mehr über die [!DNL Upgrade Compatibility Tool].

### Workflow

Das folgende Diagramm zeigt die möglichen Workflows beim Ausführen der [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Abbildung](../../assets/upgrade-guide/uct-diagram-v5.png)

### Die [!DNL Upgrade Compatibility Tool] Anwendungsfall

Im folgenden Anwendungsbeispiel wird der typische Prozess für einen Adobe Commerce-Partner zum Aktualisieren der Client-Instanz beschrieben:

1. Laden Sie die [!DNL Upgrade Compatibility Tool] Paket aus dem Adobe Commerce-Repository (`https://repo.magento.com/`). Siehe [Laden Sie die [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) für weitere Informationen.
1. Führen Sie die [!DNL Upgrade Compatibility Tool] während der [Beta](https://devdocs.magento.com/release/beta-program.html) Phase der neuesten [Adobe Commerce-Version](https://devdocs.magento.com/release/).
1. Generieren Sie eine Vanilla-Instanz für die spezifische Version von Adobe Commerce, die derzeit installiert ist. Siehe [Mitarbeiter-Handbuch](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) Weitere Informationen zur Verwendung der `instance` -Befehl, um eine Vanilla-Installation zu generieren.

   >[!NOTE]
   >
   >Eine Vanilla-Instanz ist eine saubere Installation eines angegebenen Versions-Tags oder Zweigs für eine bestimmte Release-Version.

1. Die [!DNL Upgrade Compatibility Tool] Ermittelt Probleme bei der Aktualisierung, die Software-Technikern dabei helfen, die Komplexität zu verstehen und den Aufwand für die Aktualisierung zu schätzen.
1. Diese Informationen werden mit den Interessengruppen ausgetauscht.
1. Für die Aktualisierung werden ein Budget und eine Zeitleiste festgelegt.
1. Softwareingenieure können dann an den erforderlichen Code-Änderungen arbeiten, um die fehlerhaften Module zu reparieren.
1. Die [!DNL Upgrade Compatibility Tool] kann ausgeführt werden, um den Fortschritt der Aktualisierung zu verfolgen.
1. Alles, was ausgecheckt wird, und die Technik können den Code jetzt in eine Staging-Umgebung übertragen, in der Regressionstests bestätigen, dass alle Tests grün sind. Dadurch können sie die neueste Adobe Commerce-Version am selben Tag, an dem die Adobe Commerce-Vorabversion veröffentlicht wird, in die Produktionsumgebung übernehmen.

   ![[!DNL Upgrade Compatibility Tool] audience](../../assets/upgrade-guide/audience-uct-v3.png)

### Verbessern der [!DNL Upgrade Compatibility Tool]

Verwenden Sie die folgenden Ressourcen, wenn Sie Informationen benötigen oder Fragen haben, die nicht in diesem Handbuch behandelt werden:

So stellen Sie eine Verbindung zu [!DNL Upgrade Compatibility Tool] Team, kontaktieren Sie uns im Engineering Slack-Kanal [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Wir möchten Ihr Feedback, Ihre Probleme und Anregungen hören, um uns bei der Verbesserung des Tools zu unterstützen.

Die [!DNL Upgrade Compatibility Tool] verwendet Regeln, die in unserer [Kodierungsstandards](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) , um sicherzustellen, dass Ihr Projekt die Best Practices von Adobe Commerce befolgt, und um Sie bei der Verbesserung und Erweiterung der [!DNL Upgrade Compatibility Tool].

Siehe Abschnitt [Beitragen](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  Thema für weitere Informationen zum Thema beitragende Kodierungsstandards.

### Ressourcen

Wir haben die folgenden Ressourcen entwickelt, die Ihnen beim Verständnis von Adobe Commerce-Upgrades helfen:

- [Upgrade-Handbuch](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [Bevorstehende Versionen](https://devdocs.magento.com/release/)
- [Community-Ressourcen](https://devdocs.magento.com/community/resources/resources.html) für weitere Informationen.
- [Verwandte Tools](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html)
