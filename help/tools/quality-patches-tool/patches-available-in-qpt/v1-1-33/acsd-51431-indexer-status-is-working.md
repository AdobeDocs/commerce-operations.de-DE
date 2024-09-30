---
title: "ACSD-51431: Indexerstatus ist *[!UICONTROL Working]*, auch wenn keine Einträge in der changelog vorhanden sind."
description: Wenden Sie den Patch ACSD-51431 an, um das Adobe Commerce-Problem zu beheben, bei dem der Indexstatus *[!UICONTROL Working]* ist, obwohl keine Einträge im Changelog vorhanden sind.
feature: Logs, Price Indexer
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-51431: Indexerstatus ist *[!UICONTROL Working]*, auch wenn keine Einträge im changelog vorhanden sind

Der Patch ACSD-51431 behebt das Leistungsproblem, bei dem der Indexstatus &quot;*[!UICONTROL Working]*&quot; lautet, obwohl keine Einträge in der Änderung vorhanden sind. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51431. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Indexstatus ist *[!UICONTROL Working]*, auch wenn keine Einträge in der changelog vorhanden sind.

<u>Zu reproduzierende Schritte</u>:

1. Setzen Sie **[!UICONTROL indexers]** auf [!UICONTROL Update on Schedule].
1. Konfigurieren Sie den Cron-Auftrag so, dass er jede Minute ausgeführt wird.
1. Speichern Sie Änderungen an verschiedenen Produkten gleichzeitig.
1. Führen Sie `bin/magento indexer:status` in ein paar Minuten aus.

<u>Erwartete Ergebnisse</u>:

Die Änderungen werden verarbeitet und die Indexer befinden sich im Status &quot;*[!UICONTROL Ready]*&quot;. Der *[!UICONTROL Schedule]* -Status ist *[!UICONTROL idle (0 in the backlog)]*.

<u>Tatsächliche Ergebnisse</u>:

Die Änderungen werden verarbeitet und die Indexer befinden sich im Status &quot;*[!UICONTROL Ready]*&quot;. Der Status *[!UICONTROL Schedule]* zeigt jedoch den Wert *[!UICONTROL working (0 in the backlog)]* an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
