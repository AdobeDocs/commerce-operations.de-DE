---
title: 'ACSD-54972: Kanonische Kategorie-URL wird nicht aktualisiert'
description: Wenden Sie den Patch ACSD-54972 an, um das Adobe Commerce-Problem zu beheben, bei dem die kanonische Kategorie-URL nach dem Ändern der Kategorie-URL nicht aktualisiert wird.
feature: Catalog Management, Products, Categories
role: Admin, Developer
exl-id: c4b17c08-9a2b-44a2-925e-f4c5cce7b760
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-54972: Kanonische Kategorie-URL wird nach Änderung der Kategorie-URL nicht aktualisiert

Der Patch ACSD-54972 behebt das Problem, dass die kanonische Kategorie-URL nach einer Änderung der Kategorie-URL nicht aktualisiert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 installiert ist. Die Patch-ID ist ACSD-54972. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die kanonische Kategorie-URL wird nach dem Ändern der Kategorie-URL nicht aktualisiert.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**.

   * *[!UICONTROL Use Canonical Link Meta Tag for Categories]*: *JA*

2. Erstellen Sie eine Kategorie (z. B. *Name*: *Category 01*, *URL Key*: *category-01*).
3. Aktualisieren Sie den *URL-Schlüssel* auf einen anderen Wert als den ursprünglichen, während Sie das **[!UICONTROL Create Permanent Redirect for old URL]** Kontrollkästchen aktiviert lassen.
4. Reinigen Sie den Cache.
5. Gehen Sie zum *[!UICONTROL Category Page]* im Frontend.
6. Überprüfen Sie die Seitenquelle und suchen Sie nach dem Tag *canonical*.

<u>Erwartete Ergebnisse</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01-new.html" />`

<u>Tatsächliche Ergebnisse</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01.html" />`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
