---
title: '"Integrieren Sie die [!DNL Site-Wide Analysis Tool]"'
description: Führen Sie die folgenden Schritte aus, um die [!DNL Upgrade Compatibility Tool] des [!DNL Site-Wide Analysis Tool] Dashboard Ihres Adobe Commerce-Projekts.
source-git-commit: 1fc12289125a5954243e177a0c21505234eb2e81
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Integrieren Sie die [!DNL Site-Wide Analysis Tool]

Die [!DNL Site-Wide Analysis Tool] bietet rund um die Uhr eine Leistungsüberwachung, Berichte und Empfehlungen zur Gewährleistung der Sicherheit und Bedienbarkeit von Adobe Commerce-Instanzen in Echtzeit.

Die [!DNL Upgrade Compatibility Tool] ist jetzt in die [!DNL Site-Wide Analysis Tool] um nichttechnischen Personen die Möglichkeit zu geben, die [!DNL Upgrade Compatibility Tool] und erhalten Sie [Bericht](../upgrade-compatibility-tool/reports.md) enthält eine Liste von Problemen für jede Datei.

Siehe [[!DNL Site-Wide Analysis Tool] Benutzerhandbuch](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) für weitere Informationen.

## Führen Sie die [!DNL Upgrade Compatibility Tool] von [!DNL Site-Wide Analysis Tool]

Navigieren Sie zum [!DNL Site-Wide Analysis Tool] Dashboard für Ihr Projekt und suchen Sie [!DNL Upgrade Compatibility Tool] Widget.

![UCT SWAT Widget - Ursprüngliches](../../assets/upgrade-guide/uct-swat-initial.png)

Klicken **[!UICONTROL Run Upgrade Scan]**. Die Prüfung kann abhängig von der Projektgröße einige Zeit in Anspruch nehmen. Ein Netz zeigt an, dass die Prüfung ausgeführt wird.

![UCT SWAT-Widget - Wird ausgeführt](../../assets/upgrade-guide/uct-swat-progress.png)

Nach Abschluss der Prüfung werden die Ergebnisse auf hoher Ebene im Widget angezeigt.

![UCT SWAT-Widget - Ergebnisse](../../assets/upgrade-guide/uct-swat-results.png)

Klicken **[!UICONTROL Download Report]** , um die [!DNL Upgrade Compatibility Tool] [HTML-Bericht](../upgrade-compatibility-tool/reports.md#html-report) und überprüfen Sie die Details.


>[!NOTE]
>
> Ausführen der [!DNL Upgrade Compatibility Tool] durch [!DNL Site-Wide Analysis Tool] optimiert Ihre Ergebnisse und hilft Ihnen, sich auf Probleme zu konzentrieren, die neu sind und für Ihr Ziel-Upgrade von entscheidender Bedeutung sind. Sie verwendet die [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) und zeigt immer Ergebnisse an, in denen die Version Ihres Projekts mit der neuesten veröffentlichten Version verglichen wird.
