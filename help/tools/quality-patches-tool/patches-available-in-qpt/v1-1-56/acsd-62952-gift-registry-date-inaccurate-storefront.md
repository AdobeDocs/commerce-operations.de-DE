---
title: 'ACSD-62952: Das Datum der Geschenkregistrierung wird auf der Storefront falsch angezeigt'
description: Wenden Sie den Patch ACSD-62952 an, um das Adobe Commerce-Problem zu beheben, bei dem das Geschenkregistrierungsdatum falsch auf der Storefront angezeigt wird.
feature: Gift, Storefront
role: Admin, Developer
exl-id: c11e95ab-775d-4aa7-828b-29ec52685d47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-62952: Das Datum der Geschenkregistrierung wird auf der Storefront falsch angezeigt

Mit dem Patch ACSD-62952 wird das Problem behoben, dass das Geschenkregistrierungsdatum auf der Storefront falsch angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installiert ist. Die Patch-ID ist ACSD-62952. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Ereignisdatum, das auf der Storefront für eine Shared Gift Registry angezeigt wird, wird fälschlicherweise als einen Tag vor dem tatsächlichen Datum angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Frontend als Kunde an.
1. Klicken Sie im [!UICONTROL My Account]-Dashboard auf **[!UICONTROL Gift Registry]**.
1. Wenn keine Registrierung vorhanden ist, erstellen Sie eine und geben Sie ein beliebiges Datum an.
1. Fügen Sie einen beliebigen Artikel zum Warenkorb hinzu.
1. Klicken Sie auf der Seite „Warenkorb“ auf **[!UICONTROL Add all items to Gift Registry]**.
1. Teilen Sie die Geschenkregistrierung.

<u>Erwartete Ergebnisse</u>:

Die Geschenkregistrierung zeigt das richtige Ereignisdatum an.

<u>Tatsächliche Ergebnisse</u>:

Die Geschenkregistrierung, die über die Einladungs-E-Mail geöffnet wurde, zeigt das Ereignisdatum als einen Tag früher an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: Upgrades und Patches > Anwenden von Patches im Handbuch zu Commerce in Cloud-Infrastruktur .

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
