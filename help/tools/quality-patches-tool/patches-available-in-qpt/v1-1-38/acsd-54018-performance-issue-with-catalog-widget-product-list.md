---
title: "ACSD-54018: Leistungsproblem mit Katalog-Widget-Produktliste"
description: Wenden Sie den Patch ACSD-54018 an, um das Adobe Commerce-Problem zu beheben, bei dem die Seite beim Hinzufügen einer Katalog-Widget-Produktliste mit dem booleschen Bedingungs- und Attributtyp langsam geladen wird.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-54018: Leistungsproblem mit Katalog-Widget-Produktliste

Der Patch ACSD-54018 behebt das Problem, dass die Seite beim Hinzufügen einer Katalog-Widget-Produktliste mit Bedingungen- und Attributtyp boolesch langsam geladen wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.38 installiert ist. Die Patch-ID lautet ACSD-54018. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Seite wird beim Hinzufügen einer Katalog-Widget-Produktliste mit booleschem Bedingungs- und Attributtyp langsam geladen.

<u>Zu reproduzierende Schritte</u>:

1. Generieren Sie 100.000 Produkte.
1. Erstellen Sie ein boolesches Attribut mit dem Perimeter &quot;[!UICONTROL Store View]&quot;.
1. Weisen Sie allen Attributsätzen das Attribut zu.
   * Weisen Sie allen Produkten den Attributwert *Ja* zu.
1. Gehen Sie nun zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und wählen Sie alle 100.000 Produkte aus.
   * Wählen Sie **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]** aus.
   * Setzen Sie das bool-Attribut auf *Ja* und speichern Sie es.
   * Wenn Sie sich bei diesem Schritt abgemeldet haben, überprüfen Sie die *Hinweise*.
1. Wechseln Sie zur CLI und führen Sie `php bin/magento queue:con:start product_action_attribute.update` aus.
   * Stellen Sie sicher, dass die Attribute für alle Produkte aktualisiert sind.
1. Gehen Sie nun zu **[!UICONTROL Content]** > **[!UICONTROL Pages]** und erstellen Sie eine neue Seite.
1. Öffnen Sie **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. Wählen Sie *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. Setzen Sie die Bedingung *[!UICONTROL Created attribute]* auf *[!UICONTROL Yes]* und speichern Sie sie.
1. Gehen Sie zum Frontend und öffnen Sie die erstellte Seite.
1. Deaktivieren Sie den vollständigen Seiten-Cache und blockieren Sie den HTML-Cache.
1. Überprüfen Sie die Seitenladegeschwindigkeit.
1. Laden Sie die Seite einige Male neu und berechnen Sie die durchschnittliche Ladezeit.

<u>Erwartete Ergebnisse</u>:

Die Seite wird schnell geladen.

<u>Tatsächliche Ergebnisse</u>:

Das Laden der Seite dauert 5-10 Sekunden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
