---
title: 'ACSD-45168: SEO-freundliche URLs, die nicht für Produkte generiert wurden, deren Attribute url_key überschrieben wurden'
description: Wenden Sie den Patch ACSD-45168 an, um das Adobe Commerce-Problem zu beheben, bei dem SEO-freundliche URLs nicht für Produkte generiert wurden, deren Attribute url_key auf Store-Ansichtsebene überschrieben wurden.
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
exl-id: 7d908307-f60c-4758-ad0f-f108ebb94558
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-45168: SEO-freundliche URLs, die nicht für Produkte generiert wurden, deren Attribute url_key überschrieben wurden

Der Patch ACSD-45168 behebt das Problem, dass SEO-freundliche URLs nicht für Produkte generiert werden, deren Attribute url_key auf der Store-Ansichtsebene überschrieben werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-45168. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

SEO-freundliche URLs werden nicht für Produkte generiert, bei denen url_key -Attribute auf der Store-Ansichtsebene überschrieben werden.

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie die Konfiguration wie folgt ein, indem Sie zu **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** gehen:
   * [!UICONTROL Use Categories Path for Product URLs] = *Ja*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Ja*
1. Bereinigen Sie den Konfigurations-Cache.
1. Erstellen Sie zwei Kategorien: [!UICONTROL Category 1] und [!UICONTROL Category 2].
1. Erstellen Sie zwei Produkte: [!UICONTROL Product 1] in [!UICONTROL Category 1], [!UICONTROL Product 2] in [!UICONTROL Category 1].
1. Ändern Sie den Umfang für [!UICONTROL Product 1] in [!UICONTROL Default Store View].
1. Deaktivieren Sie die optionale URL [!UICONTROL Key] in [!UICONTROL Search Engine Optimization].
1. Speichern Sie das Produkt.
1. Wechseln Sie zurück zu [!UICONTROL All Store Views].
1. Fügen Sie [!UICONTROL Product 1] zu [!UICONTROL Category 2] hinzu und fügen Sie [!UICONTROL Product 2] zu [!UICONTROL Category 2] hinzu.
1. Überprüfen Sie die Tabelle `url_rewrite` oder die Tabelle [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Erwartete Ergebnisse</u>:

Die SEO-freundliche URL für [!UICONTROL Category 2] wird für [!UICONTROL Product 1] erstellt.

<u>Tatsächliche Ergebnisse</u>:

Die SEO-freundliche URL für [!UICONTROL Category 2] fehlt für [!UICONTROL Product 1], da das URL-Schlüsselattribut für den Umfang der Store-Ansicht überschrieben wurde.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool]-Handbuch, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
