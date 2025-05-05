---
title: 'ACSD-54018: Leistungsproblem mit der Produktliste des Katalog-Widgets'
description: Wenden Sie den Patch ACSD-54018 an, um das Adobe Commerce-Problem zu beheben, dass die Seite beim Hinzufügen einer Katalog-Widget-Produktliste mit booleschen Werten für Bedingung und Attributtyp langsam geladen wird.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 2fb7ca37-78cc-45f4-86a3-d922cf4d1457
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-54018: Leistungsproblem mit der Produktliste des Katalog-Widgets

Der Patch ACSD-54018 behebt das Problem, dass die Seite beim Hinzufügen einer Katalog-Widget-Produktliste mit booleschen Bedingungen und Attributtypen langsam geladen wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.38 installiert ist. Die Patch-ID ist ACSD-54018. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Seite wird beim Hinzufügen einer Katalog-Widget-Produktliste mit booleschem Wert für Bedingung und Attributtyp langsam geladen.

<u>Schritte zur Reproduktion</u>:

1. Generieren Sie 100.000 Produkte.
1. Erstellen Sie ein bool-Attribut mit dem Bereich [!UICONTROL Store View].
1. Weisen Sie allen Attributsätzen das Attribut zu.
   * Weisen Sie den Attributwert *Ja* allen Produkten zu.
1. Navigieren Sie nun zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und wählen Sie alle 100.000 Produkte aus.
   * Wählen Sie **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * Setzen Sie das Attribut bool auf *Yes* und speichern Sie es.
   * Wenn Sie sich bei diesem Schritt abgemeldet haben, überprüfen Sie die *Hinweise*.
1. Wechseln Sie zu CLI und führen Sie `php bin/magento queue:con:start product_action_attribute.update` aus.
   * Stellen Sie sicher, dass die Attribute für alle Produkte aktualisiert werden.
1. Gehen Sie nun zu **[!UICONTROL Content]** > **[!UICONTROL Pages]** und erstellen Sie eine neue Seite.
1. Öffnen Sie **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. Wählen Sie *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. Setzen Sie den *[!UICONTROL Created attribute]* auf *[!UICONTROL Yes]* und speichern Sie ihn.
1. Wechseln Sie zum Frontend und öffnen Sie die erstellte Seite.
1. Deaktivieren Sie den vollständigen Seiten-Cache und den HTML-Cache blockieren.
1. Überprüfen Sie die Seitenladegeschwindigkeit.
1. Laden Sie die Seite einige Male neu und berechnen Sie die durchschnittliche Ladezeit.

<u>Erwartete Ergebnisse</u>:

Die Seite wird schnell geladen.

<u>Tatsächliche Ergebnisse</u>:

Das Laden der Seite dauert 5-10 Sekunden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
