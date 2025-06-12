---
title: 'ACSD-56979: Nach Staging-Update entfernte Produktbilder gelöscht'
description: Wenden Sie den ACSD-56979-Patch an, um das Adobe Commerce-Problem zu beheben, dass Produktbilder nach dem Löschen eines Staging-Updates entfernt werden
feature: Products
role: Admin, Developer
exl-id: 1e0fbd5c-285b-408e-ba52-72619e29167b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-56979: Nach Staging-Update entfernte Produktbilder gelöscht

Mit dem Patch ACSD-56979 wird das Problem behoben, dass Produktbilder nach dem Löschen einer Staging-Aktualisierung entfernt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-56979. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce- und Magento Open Source-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Produktbilder werden nach dem Löschen einer Staging-Aktualisierung entfernt.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie in der Commerce Admin -Seitenleiste zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und erstellen Sie ein Produkt.
1. Laden Sie unter **[!UICONTROL Images and Videos]** ein Bild hoch und speichern Sie das Produkt.
1. Wählen Sie im **[!UICONTROL Scheduled Changes]** die Option **[!UICONTROL Schedule New Update]** aus.
   1. Wählen Sie ein Startdatum einige Minuten später aus.
   1. Kein Enddatum auswählen.
1. Klicken Sie im **[!UICONTROL Scheduled Changes]** auf den Link **[!UICONTROL View/Edit]** .
1. Navigieren Sie zu **[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]** und wählen Sie **[!UICONTROL Done]**.
1. Aktualisieren Sie die Seite.

<u>Erwartete Ergebnisse</u>:

Da das Update vor dem geplanten Startdatum entfernt wird, sollte das Produkt unverändert bleiben.

<u>Tatsächliche Ergebnisse</u>:

Der Bildinhalt geht verloren und zeigt null Bytes an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
