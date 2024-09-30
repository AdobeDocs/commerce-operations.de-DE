---
title: '"ACSD-57074: *Ja/Nein* benutzerdefiniertes Attribut mit dem Präfix "price_*"im Attribut "attribute_code"funktioniert nicht mit der Indizierung."'
description: Wenden Sie den Patch ACSD-57074 an, um das Adobe Commerce-Problem zu beheben, bei dem das benutzerdefinierte Attribut *Ja/Nein* mit dem Präfix `price_* im Attribut `attribute_code` nicht mit der Indizierung funktioniert.
feature: Products, Categories, Catalog Management
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-57074: *Ja/Nein* Benutzerdefiniertes Attribut mit dem Präfix `price_*` im Attribut `attribute_code` funktioniert nicht bei der Indizierung

Der Patch ACSD-57074 behebt das Problem, dass das benutzerdefinierte Attribut *Ja/Nein* mit dem Präfix `price_*` im Attribut `attribute_code` bei der Indizierung nicht funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.47 installiert ist. Die Patch-ID ist ACSD-57074. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das benutzerdefinierte Attribut *Ja/Nein* mit dem Präfix `price_*` im Attribut `attribute_code` funktioniert nicht bei der Indizierung.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein benutzerdefiniertes Produktattribut mit den folgenden Optionen:
   * *[!UICONTROL Catalog Input Type]*: *Ja/Nein*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *Ja*
1. Weisen Sie das Attribut dem standardmäßigen Attributsatz zu.
1. Erstellen Sie ein Produkt mit dem von uns erstellten Attribut.
1. Weisen Sie das soeben erstellte Produkt einer Kategorie zu.
1. Führen Sie die vollständige Neuindizierung aus.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird in der zugewiesenen Kategorie angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird nicht auf der Titelkategorieseite angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
