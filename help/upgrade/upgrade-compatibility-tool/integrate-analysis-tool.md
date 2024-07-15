---
title: Integrieren von  [!DNL Site-Wide Analysis Tool]
description: Führen Sie die folgenden Schritte aus, um den Bericht [!DNL Upgrade Compatibility Tool] vom [!DNL Site-Wide Analysis Tool] Dashboard in Ihrem Adobe Commerce-Projekt abzurufen.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Integrieren von [!DNL Site-Wide Analysis Tool]

Der [!DNL Site-Wide Analysis Tool] bietet rund um die Uhr eine Leistungsüberwachung, Berichte und Empfehlungen zur Überwachung der Echtzeitleistung, um die Sicherheit und Bedienbarkeit für Adobe Commerce-Instanzen sicherzustellen.

Der [!DNL Upgrade Compatibility Tool] ist jetzt in den [!DNL Site-Wide Analysis Tool] integriert, um nichttechnischen Personen die Möglichkeit zu geben, den [!DNL Upgrade Compatibility Tool] auszuführen und einen [Bericht](../upgrade-compatibility-tool/reports.md) mit einer Liste von Problemen für jede Datei zu erhalten.

Weitere Informationen finden Sie im [[!DNL Site-Wide Analysis Tool] Benutzerhandbuch](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) .

## Führen Sie die [!DNL Upgrade Compatibility Tool] aus der [!DNL Site-Wide Analysis Tool] aus.

Navigieren Sie zum Dashboard [!DNL Site-Wide Analysis Tool] für Ihr Projekt und suchen Sie das Widget [!DNL Upgrade Compatibility Tool] .

![UCT SWAT widget - Initial](../../assets/upgrade-guide/uct-swat-initial.png)

Klicken Sie auf **[!UICONTROL Run Upgrade Scan]**. Die Prüfung kann abhängig von der Projektgröße einige Zeit in Anspruch nehmen. Ein Netz zeigt an, dass die Prüfung ausgeführt wird.

![UCT SWAT widget - In Bearbeitung](../../assets/upgrade-guide/uct-swat-progress.png)

Nach Abschluss der Prüfung werden die Ergebnisse auf hoher Ebene im Widget angezeigt.

![UCT SWAT widget - Results](../../assets/upgrade-guide/uct-swat-results.png)

Klicken Sie auf **[!UICONTROL Download Report]** , um den Bericht [!DNL Upgrade Compatibility Tool] [HTML](../upgrade-compatibility-tool/reports.md#html-report) abzurufen und die Details zu überprüfen.


>[!NOTE]
>
> Wenn Sie die [!DNL Upgrade Compatibility Tool] durch die [!DNL Site-Wide Analysis Tool] ausführen, werden Ihre Ergebnisse optimiert und Sie können sich auf Probleme konzentrieren, die neu sind und für Ihr Ziel-Upgrade von entscheidender Bedeutung sind. Sie verwendet die Option &quot;[`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results)&quot; und zeigt immer Ergebnisse an, in denen die Version Ihres Projekts mit der neuesten veröffentlichten Version verglichen wird.
