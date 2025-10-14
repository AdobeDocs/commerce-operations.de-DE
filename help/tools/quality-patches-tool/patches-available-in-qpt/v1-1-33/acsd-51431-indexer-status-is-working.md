---
title: 'ACSD-51431: Indexerstatus ist *[!UICONTROL Working]* auch wenn im Änderungsprotokoll keine Einträge vorhanden sind'
description: Wenden Sie den Patch ACSD-51431 an, um das Adobe Commerce-Problem zu beheben, bei dem der Indexerstatus *[!UICONTROL Working]* lautet, obwohl im Änderungsprotokoll keine Einträge vorhanden sind.
feature: Logs, Price Indexer
role: Admin
exl-id: c87c059b-f435-468d-a7fe-e6786fdba1f8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-51431: Indexerstatus ist *[!UICONTROL Working]*, obwohl es keine Einträge im Änderungsprotokoll gibt

Mit dem Patch ACSD-51431 wird das Leistungsproblem behoben, bei dem der Indexerstatus *[!UICONTROL Working]* ist, obwohl im Änderungsprotokoll keine Einträge vorhanden sind. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51431. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Indexerstatus ist *[!UICONTROL Working]*, auch wenn im Änderungsprotokoll keine Einträge vorhanden sind.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie **[!UICONTROL indexers]** auf [!UICONTROL Update on Schedule] fest.
1. Konfigurieren Sie den Cron-Auftrag so, dass er jede Minute ausgeführt wird.
1. Änderungen an verschiedenen Produkten gleichzeitig speichern.
1. Führen Sie `bin/magento indexer:status` in ein paar Minuten aus.

<u>Erwartete Ergebnisse</u>:

Die Änderungen werden verarbeitet und die Indexer befinden sich im Status *[!UICONTROL Ready]* . Der *[!UICONTROL Schedule]* ist *[!UICONTROL idle (0 in the backlog)]*.

<u>Tatsächliche Ergebnisse</u>:

Die Änderungen werden verarbeitet und die Indexer befinden sich im Status *[!UICONTROL Ready]* . Der *[!UICONTROL Schedule]* wird jedoch *[!UICONTROL working (0 in the backlog)]* angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
