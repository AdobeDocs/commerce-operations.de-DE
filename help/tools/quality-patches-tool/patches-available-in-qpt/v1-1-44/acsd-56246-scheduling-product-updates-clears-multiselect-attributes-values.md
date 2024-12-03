---
title: 'ACSD-56246: Durch die Planung von Produktaktualisierungen werden die Mehrfachauswahlattributwerte gelöscht.'
description: Wenden Sie den Patch ACSD-56246 an, um das Adobe Commerce-Problem zu beheben, bei dem durch die Planung von Produktaktualisierungen die Multiselect-Attributwerte gelöscht werden.
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: 1751a03d-2610-423f-be2f-b9d060452904
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-56246: Bei der Planung von Produktaktualisierungen werden Werte für Mehrfachauswahl-Attribute gelöscht

Der Patch ACSD-56246 behebt das Problem, dass durch die Planung von Produktaktualisierungen Werte für Mehrfachauswahl-Attribute gelöscht werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 installiert ist. Die Patch-ID ist ACSD-56246. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die geplanten Produktaktualisierungen löschen die Multiselect-Attributwerte.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und erstellen Sie das folgende Attribut:

   * Standardbezeichnung: Programm
   * Katalogeingabetyp für Store Owner: Mehrfachauswahl
   * Optionen verwalten (Werte Ihres Attributs): Auswahl, Querformat, SafetyShield
   * Attributcode: customer_program
   * Umfang: Global
   * Zu Spaltenoptionen hinzufügen: Nein
   * Verwendung in Filteroptionen: nein
   * Store-Eigenschaften
   * Position: *333*
   * HTML-Tags in der Storefront zulassen: nein

1. Ausführen
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Ausführen
   `bin/magento setup:upgrade`.
1. Gehen Sie zu &quot;**[!UICONTROL Admin]**&quot;> &quot;Einfaches Produkt auswählen&quot;> &quot;Alle Elemente im Programmattribut auswählen&quot;> &quot;Klicken Sie auf &quot;**[!UICONTROL Save the product]**&quot;.
1. Planen Sie ein Update für dieses Produkt in der nächsten Minute und führen Sie den folgenden Befehl aus, um die Inhaltsstaging-Umgebung zu nutzen:
   `for i in {1..100}; do bin/magento cron:run; done`.

<u>Erwartete Ergebnisse</u>:

Das Attribut **[!UICONTROL program]** des Produkts sollte sich nicht ändern.

<u>Tatsächliche Ergebnisse</u>:

Das Attribut **[!UICONTROL program]** des Produkts wird gelöscht.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
