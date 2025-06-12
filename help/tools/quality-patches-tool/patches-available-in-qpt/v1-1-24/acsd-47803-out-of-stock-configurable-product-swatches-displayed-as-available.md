---
title: 'ACSD-47803: Nicht vorrätige konfigurierbare Produktmuster werden als verfügbar angezeigt'
description: Wenden Sie den ACSD-47803-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem nicht vorrätige konfigurierbare Produktmuster als verfügbar angezeigt werden.
feature: Configuration, Orders, Products
role: Admin
exl-id: c1b80949-65ed-4a44-8be4-25decda32142
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-47803: Nicht vorrätige konfigurierbare Produktmuster werden als verfügbar angezeigt

Mit dem Patch ACSD-47803 wird das Problem behoben, dass nicht mehr vorrätige konfigurierbare Produktmuster als verfügbar angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-47803. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nicht vorrätige konfigurierbare Produktmuster werden nach Verfügbarkeit angezeigt.

<u>Schritte zur Reproduktion</u>:

>[!NOTE]
>
>Die folgenden Schritte beziehen sich auf Beispieldaten als Beispiel.

1. Gehen Sie im [!UICONTROL Commerce] Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** und legen Sie die **[!UICONTROL Display Out of Stock Products]** auf *Ja* fest.
1. Navigieren Sie wiederum vom Administrator aus zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und bearbeiten Sie ein konfigurierbares Produkt auf der Seite zur Produktbearbeitung (z. B. „WB04“-SKU, wenn Sie Beispieldaten verwenden):
   * Stellen Sie für eine der Konfigurationsvarianten die Menge auf *0* ein (z. B. für „WB04-M-Purple„).
1. Öffnen Sie jetzt das konfigurierbare Produkt in der Storefront.
1. Wählen Sie die Produktgröße für die konfigurierbare Variante mit null Lager (d. h. „M„).

<u>Erwartete Ergebnisse</u>:

Die nicht vorrätigen Optionen sind deaktiviert und als [!UICONTROL Out of Stock] gekennzeichnet.

<u>Tatsächliche Ergebnisse</u>:

Alle Farbfelder sind aktiviert, auch das [!UICONTROL Out of Stock] Farbfeld.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
