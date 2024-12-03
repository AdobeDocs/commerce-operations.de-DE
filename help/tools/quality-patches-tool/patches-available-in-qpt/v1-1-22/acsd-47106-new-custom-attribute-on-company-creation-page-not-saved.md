---
title: 'ACSD-47106: neues benutzerdefiniertes Attribut auf der Seite zur Unternehmenserstellung nicht gespeichert'
description: Wenden Sie den Patch ACSD-47106 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Wert nicht in einem neuen benutzerdefinierten Attribut auf einer Seite zur Unternehmenserstellung gespeichert werden kann.
feature: Attributes, B2B, Companies
role: Developer
exl-id: 5835760d-fca1-44ba-aa5e-8797258c7c75
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47106: neues benutzerdefiniertes Attribut auf der Seite zur Unternehmenserstellung nicht gespeichert

Der Patch ACSD-47106 behebt das Problem, dass ein Wert nicht in einem neuen benutzerdefinierten Attribut auf einer Seite zur Unternehmenserstellung gespeichert werden kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22 installiert ist. Die Patch-ID ist ACSD-47106. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Wert kann nicht in einem neuen benutzerdefinierten Attribut auf einer Seite zur Unternehmenserstellung gespeichert werden.

<u>Voraussetzungen</u>:

* B2B-Module sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Customer]** > **[!UICONTROL Add New Attribute]**.
1. Erstellen Sie ein neues Attribut: _Test 01_.
1. Gehen Sie zu Commerce Admin > **[!UICONTROL Customers]** > **[!UICONTROL Companies]** > und erstellen Sie ein neues Unternehmen mit allen erforderlichen Details.
1. Versuchen Sie, dem benutzerdefinierten Attribut _Test 01_ einen Wert hinzuzufügen.
1. Versuchen Sie, den Wert des benutzerdefinierten Attributs _Test 01_ zu aktualisieren.

<u>Erwartete Ergebnisse</u>:

Änderungen werden gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Änderungen werden nicht gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
