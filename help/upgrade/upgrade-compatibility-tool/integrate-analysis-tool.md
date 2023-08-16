---
title: Integrieren Sie die [!DNL Site-Wide Analysis Tool]
description: Führen Sie die folgenden Schritte aus, um die [!DNL Upgrade Compatibility Tool] des [!DNL Site-Wide Analysis Tool] Dashboard Ihres Adobe Commerce-Projekts.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Integrieren Sie die [!DNL Site-Wide Analysis Tool]

Die [!DNL Site-Wide Analysis Tool] bietet rund um die Uhr eine Leistungsüberwachung, Berichte und Empfehlungen in Echtzeit, um die Sicherheit und Bedienbarkeit von Adobe Commerce-Instanzen sicherzustellen.

Die [!DNL Upgrade Compatibility Tool] ist jetzt in die [!DNL Site-Wide Analysis Tool] um nichttechnischen Personen die Möglichkeit zu geben, die [!DNL Upgrade Compatibility Tool] und erhalten Sie [Bericht](../upgrade-compatibility-tool/reports.md) enthält eine Liste von Problemen für jede Datei.

Siehe [[!DNL Site-Wide Analysis Tool] Benutzerhandbuch](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) für weitere Informationen.

## Führen Sie die [!DNL Upgrade Compatibility Tool] aus dem [!DNL Site-Wide Analysis Tool]

Navigieren Sie zum [!DNL Site-Wide Analysis Tool] Dashboard für Ihr Projekt und suchen Sie nach [!DNL Upgrade Compatibility Tool] Widget.

![UCT SWAT Widget - Ursprüngliches](../../assets/upgrade-guide/uct-swat-initial.png)

Klicken **[!UICONTROL Run Upgrade Scan]**. Die Prüfung kann abhängig von der Projektgröße einige Zeit in Anspruch nehmen. Ein Netz zeigt an, dass die Prüfung ausgeführt wird.

![UCT SWAT-Widget - Wird ausgeführt](../../assets/upgrade-guide/uct-swat-progress.png)

Nach Abschluss der Prüfung werden die Ergebnisse auf hoher Ebene im Widget angezeigt.

![UCT SWAT-Widget - Ergebnisse](../../assets/upgrade-guide/uct-swat-results.png)

Klicks **[!UICONTROL Download Report]** , um die [!DNL Upgrade Compatibility Tool] [HTML-Bericht](../upgrade-compatibility-tool/reports.md#html-report) und überprüfen Sie die Details.


>[!NOTE]
>
> Ausführen der [!DNL Upgrade Compatibility Tool] durch die [!DNL Site-Wide Analysis Tool] optimiert Ihre Ergebnisse und hilft Ihnen, sich auf Probleme zu konzentrieren, die neu sind und für Ihr Ziel-Upgrade von entscheidender Bedeutung sind. Sie verwendet die [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) und zeigt immer Ergebnisse an, in denen die Version Ihres Projekts mit der neuesten veröffentlichten Version verglichen wird.
