---
title: 'ACSD-54972: Kanonische Kategorie-URL wird nicht aktualisiert'
description: Wenden Sie den Patch ACSD-54972 an, um das Adobe Commerce-Problem zu beheben, bei dem die kanonische Kategorie-URL nicht aktualisiert wird, nachdem die Kategorie-URL geändert wurde.
feature: Catalog Management, Products, Categories
role: Admin, Developer
exl-id: c4b17c08-9a2b-44a2-925e-f4c5cce7b760
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-54972: Die kanonische Kategorie-URL wird nach Änderung der Kategorie-URL nicht aktualisiert

Der Patch ACSD-54972 behebt das Problem, dass die kanonische Kategorie-URL nach dem Ändern der Kategorie-URL nicht aktualisiert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 installiert ist. Die Patch-ID ist ACSD-54972. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die kanonische Kategorie-URL wird nach Änderung der Kategorie-URL nicht aktualisiert.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**.

   * Legen Sie *[!UICONTROL Use Canonical Link Meta Tag for Categories]*: *YES* fest.

2. Erstellen Sie eine Kategorie (z. B. *Name*: *Kategorie 01*, *URL-Schlüssel*: *Kategorie-01*).
3. Aktualisieren Sie den *URL-Schlüssel* so, dass er sich vom ursprünglichen Wert unterscheidet, während Sie das Kontrollkästchen **[!UICONTROL Create Permanent Redirect for old URL]** angekreuzt halten.
4. Bereinigen Sie den Cache.
5. Wechseln Sie zur &quot;*[!UICONTROL Category Page]*&quot; am Frontend.
6. Überprüfen Sie die Seitenquelle und suchen Sie nach dem Tag *canonical* .

<u>Erwartete Ergebnisse</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01-new.html" />`

<u>Tatsächliche Ergebnisse</u>:

`<link rel="canonical" href="http://127.0.0.1/pub/category-01.html" />`

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
