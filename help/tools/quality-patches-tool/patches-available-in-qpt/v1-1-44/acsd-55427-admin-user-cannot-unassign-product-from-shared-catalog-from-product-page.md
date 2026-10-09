---
title: 'ACSD-55427: Ein Administrator kann die Zuweisung von Produkt zu **[!UICONTROL Product in Shared Catalogs]** auf der Produktseite nicht aufheben'
description: Wenden Sie den ACSD-55427 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Zuweisung eines Produkts zu **[!UICONTROL Product in Shared Catalogs]** nicht aufgehoben werden kann.
feature: Products, B2B
role: Admin, Developer
exl-id: 974347fd-351d-4a4b-a9ca-a534daf3fbd7
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%
---
# ACSD-55427: Ein Administrator kann die Zuweisung von **[!UICONTROL Product in Shared Catalogs]** auf der Produktseite nicht aufheben

Mit dem Patch ACSD-55427 wird das Problem behoben, dass Sie die Zuweisung eines Produkts zu **[!UICONTROL Product in Shared Catalogs]** auf der Produktseite im Katalog in Commerce Admin nicht aufheben können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.44 installiert ist. Die Patch-ID ist ACSD-55427. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Zuweisung eines Produkts zu einem **[!UICONTROL Product in Shared Catalogs]** auf der Produktseite im Katalog im Commerce-Admin-Bereich kann nicht aufgehoben werden.

<u>Schritte zur Reproduktion</u>:

Voraussetzungen: Adobe Commerce muss mit aktiviertem B2B- und **[!UICONTROL Shared Catalogs]** installiert werden.
1. Erstellen Sie ein Produkt.
1. Navigieren Sie zum Dashboard des freigegebenen Katalogs und öffnen Sie den standardmäßigen freigegebenen Katalog.
1. Das Produkt dem Standardkatalog zuweisen und einen Preis festlegen, der unter dem Produktpreis liegt.
1. Speichern Sie den freigegebenen Katalog.
1. Führen Sie die [!UICONTROL CRON] aus, um die Verbraucher/Indexer zu aktualisieren.
1. Öffnen Sie das Produkt und entfernen Sie das Produkt aus **[!UICONTROL Product in Shared Catalogs]** Abschnitt.

<u>Erwartete Ergebnisse</u>:

Das Produkt ist aus dem Abschnitt **[!UICONTROL Product in Shared Catalogs]** zu entfernen.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird weiterhin im Abschnitt **[!UICONTROL Product in Shared Catalogs]** angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
