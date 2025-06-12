---
title: 'ACSD-47336: [!UICONTROL Something went wrong] beim Verwerfen von Benachrichtigungen in Adobe Commerce Admin'
description: Wenden Sie den Patch „ACSD-47336 [!UICONTROL Something went wrong]" an, um das Problem in Adobe Commerce zu beheben, bei dem beim Verwerfen von Benachrichtigungen in "-admin [!DNL Commerce]  der Fehler angezeigt wird.
feature: Admin Workspace
role: Admin
exl-id: da0c0119-6720-493f-a278-d573ed898a63
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47336: _[!UICONTROL Something went wrong]_&#x200B;beim Verwerfen von Benachrichtigungen in Adobe Commerce Admin

Mit dem Patch „ACSD-47336“ wird das Problem behoben, dass beim Verwerfen von Benachrichtigungen in der [!DNL Commerce] Admin der _[!UICONTROL Something went wrong]_&#x200B;Fehler angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-47336. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden): 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der/die Benutzende sieht _[!UICONTROL Something went wrong]_&#x200B;Fehler, wenn er/sie die Benachrichtigungen im [!DNL Commerce] Admin verwirft.

<u>Schritte zur Reproduktion</u>:

1. Führen Sie einen Massenvorgang durch (z. B. eine Massenaktualisierung von Produktattributen aus dem Produktraster).
1. Schließen Sie den Vorgang ab (z. B. `bin/magento queue:consumer:start product_action_attribute.update` ausführen).
1. Aktualisieren Sie die Seite &quot;[!DNL Commerce] Admin“, erweitern Sie den Abschnitt „Admin-Benachrichtigung“ und klicken Sie auf den Link **[!UICONTROL Dismiss All Completed Tasks]** .

<u>Erwartete Ergebnisse</u>:

Der _[!UICONTROL Something went wrong]_&#x200B;sollte beim Löschen der abgeschlossenen Aufgaben nicht angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Der _[!UICONTROL Something went wrong]_&#x200B;wird angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
