---
title: 'ACSD-46809: Beim Zuweisen einer großen Anzahl von Produktquellen erhält der Benutzer einen Fehler'
description: Wenden Sie den Patch ACSD-46809 an, um das Adobe Commerce-Problem zu beheben, bei dem der Benutzer beim Zuweisen einer großen Anzahl von Produktquellen einen Fehler erhält.
feature: Products
role: Admin
exl-id: 4225f49b-84a1-4641-a05b-ba6ada6e83be
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# ACSD-46809: Beim Zuweisen einer großen Anzahl von Produktquellen erhält der Benutzer einen Fehler

Der Patch ACSD-46809 behebt das Problem, bei dem der Benutzer beim Zuweisen einer großen Anzahl von Produktquellen einen Fehler erhält. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.21 installiert ist. Die Patch-ID ist ACSD-46809. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Zuweisen einer großen Anzahl von Produktquellen erhält der Benutzer einen Fehler.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie mehr als 200 benutzerdefinierte Quellen.
1. Navigieren Sie zu Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Bearbeiten Sie ein beliebiges Produkt.
1. Weisen Sie diesem Produkt gleichzeitig 200 Quellen zu.

<u>Erwartete Ergebnisse</u>:

Dem Produkt werden 200 Quellen ohne Fehler zugewiesen.

<u>Tatsächliche Ergebnisse</u>:

*Es wird ein Fehler angezeigt*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
