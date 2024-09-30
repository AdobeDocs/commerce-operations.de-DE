---
title: "ACSD-54961: Eingeschränkte Administratoren können keine Massenaktualisierung durchführen [!UICONTROL Product Review status]"
description: Wenden Sie den Patch ACSD-54961 an, um das Adobe Commerce-Problem zu beheben, bei dem ein eingeschränkter Admin-Benutzer den Status Produktprüfung nicht gebündelt aktualisieren kann.
feature: Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54961: Eingeschränkte Administratoren können keine Massenaktualisierung durchführen [!UICONTROL Product Review status]

Der Patch ACSD-54961 behebt das Problem, dass ein eingeschränkter Administrator kein Massenupdate [!UICONTROL Product Review status] durchführen kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-54961. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein eingeschränkter Administrator kann keine Massenaktualisierung von [!UICONTROL Product Review status] vornehmen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Website-, Store- und Store-Ansicht.
1. Fügen Sie ein Produkt zum zweiten Store hinzu und fügen Sie dann eine Überprüfung hinzu.
1. Erstellen Sie einen eingeschränkten Administratorbenutzer mit Zugriff nur auf den zweiten Store.
1. Melden Sie sich als eingeschränkter Admin-Benutzer an, wechseln Sie dann zu &quot;**[!UICONTROL  Marketings]**&quot;> &quot;**[!UICONTROL Reviews]**&quot;> &quot;**[!UICONTROL Mass Update]**&quot;und legen Sie den &quot;**Status**&quot;auf &quot;*Genehmigt*&quot;oder &quot;*Ausstehend*&quot;fest.

<u>Erwartete Ergebnisse</u>:

Der eingeschränkte Admin-Benutzer kann Bewertungen mit der Aktion **[!UICONTROL Mass Update]** aktualisieren.

<u>Tatsächliche Ergebnisse</u>:

Beim Aktualisieren von Überprüfungen mit der Aktion **[!UICONTROL Mass Update]** tritt ein Fehler auf.<br>
Der `var/log/exception.log` enthält einen ähnlichen Fehler:

```
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
