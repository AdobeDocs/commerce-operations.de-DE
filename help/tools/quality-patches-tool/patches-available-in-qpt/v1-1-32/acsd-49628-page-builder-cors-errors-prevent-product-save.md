---
title: 'ACSD-49628: [!DNL Page Builder] CORS-Fehler verhindern das Speichern des Produkts'
description: Wenden Sie den ACSD-49628-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die  [!DNL Page Builder] -CORS-Fehler das Speichern des Produkts verhindern.
feature: Categories, Page Builder, Products
role: Admin
exl-id: 5bceddfa-5fbf-4ebe-a233-de7720764849
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-49628: [!DNL Page Builder] CORS-Fehler verhindern das Speichern von Produkten

Mit dem Patch ACSD-49628 wird das Problem behoben, dass [!DNL Page Builder] CORS-Fehler einen Administrator daran hindern, ein Produkt zu speichern. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-49628. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL Page Builder] CORS-Fehler verhindern das Speichern eines Produkts.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich als Administrator an.
1. Erstellen Sie eine Benutzerrolle mit den folgenden Berechtigungen:

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. Fügen Sie keine *[!UICONTROL Content]* Berechtigungen hinzu.
1. Erstellen Sie einen weiteren Admin-Benutzer und weisen Sie diesem Benutzer die oben erstellten Rollen zu.
1. Erstellen Sie ein Produkt und melden Sie sich ab.
1. Melden Sie sich als zweiter Administrator an.
1. Versuchen Sie, das Produkt zu bearbeiten und zu speichern.

<u>Erwartete Ergebnisse</u>:

Der zweite Administrator kann das Produkt speichern, aber der Administrator erhält keine **[!UICONTROL Edit with Page Builder]** Berechtigungen für die Schaltfläche *[!UICONTROL Content]*.

<u>Tatsächliche Ergebnisse</u>:

Der zweite Administrator kann das Produkt aufgrund mehrerer [!DNL Page Builder] nicht speichern.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
