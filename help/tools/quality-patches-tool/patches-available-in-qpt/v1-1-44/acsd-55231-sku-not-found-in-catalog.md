---
title: "ACSD-55231: SKU bei Verwendung der Funktion für schnelle Bestellungen nicht gefunden Fehler"
description: Wenden Sie den Patch ACSD-55231 an, um das Adobe Commerce-Problem zu beheben, bei dem Sie die Fehlermeldung *'Die SKU wurde nicht im Katalog gefunden'* erhalten, wenn Sie versuchen, ein Produkt mithilfe der Funktion für schnelle Bestellungen zum Warenkorb hinzuzufügen.
feature: Products, Checkout, B2B
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-55231: SKU konnte bei Verwendung der Funktion für schnelle Bestellungen keinen Fehler finden

Der Patch ACSD-55231 behebt das Problem, dass Sie *&#39;Die SKU wurde nicht im Fehler* des Katalogs gefunden haben, wenn Sie versuchen, ein Produkt mithilfe der Funktion für schnelle Bestellungen zum Warenkorb hinzuzufügen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 installiert ist. Die Patch-ID ist ACSD-55231. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Abrufen von *&#39;der SKU wurde nicht im Fehler* des Katalogs gefunden, wenn Sie nach Produkten suchen, die mithilfe der Funktion für schnelle Bestellungen zum Warenkorb hinzugefügt werden sollen.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce mit B2B-Modulen.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** und legen Sie Folgendes fest:
   * **[!UICONTROL Enable company]**: *Ja*
   * **[!UICONTROL Enable Shared Catalog]**: *Ja*
   * **[!UICONTROL Enable Quick Order]**: *Ja*
1. Speichern Sie die oben beschriebene Konfiguration.
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** und erstellen Sie einen neuen freigegebenen Katalog.
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** und erstellen Sie einen neuen Kunden:
   * Wählen Sie im Gruppenfeld den kürzlich erstellten freigegebenen Katalog aus und setzen Sie *[!UICONTROL Allow remote shopping assistance]* auf *Ja*.
1. Generieren Sie ein einfaches Produkt mit SKU *p12*, verknüpfen Sie es mit der Kategorie *c1* und wählen Sie dann den neu erstellten freigegebenen Katalog im Abschnitt [!UICONTROL Product in Shared Catalog] aus.
1. Ausführen:

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. Aktualisieren Sie die Admin-Seite.
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** und bearbeiten Sie den zuvor erstellten Kunden.
1. Klicken Sie auf **[!UICONTROL Login as customer]**.
1. Wechseln Sie zu &quot;**[!UICONTROL Quick order]**&quot;.
1. Durchsuchen Sie die SKU *p12* und klicken Sie auf die **[!UICONTROL Product Suggestion]**.
1. Fügen Sie dieses Produkt zum Warenkorb hinzu und geben Sie die Bestellung auf.
1. Kehren Sie zu **[!UICONTROL Quick Order]** zurück, suchen Sie erneut nach SKU *p12* und klicken Sie auf **[!UICONTROL Product Suggestion]**.

<u>Erwartete Ergebnisse</u>:

Sie können das Produkt mithilfe der Funktion für schnelle Bestellungen zum Warenkorb hinzufügen.

<u>Tatsächliche Ergebnisse</u>:

Sie können das Produkt nicht mithilfe der Funktion für schnelle Bestellungen zum Warenkorb hinzufügen und erhalten den Fehler *&#39;Die SKU wurde nicht im Katalog&#39;* bei der Suche nach der Produkt-SKU gefunden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
