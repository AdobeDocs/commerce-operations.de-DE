---
title: 'ACSD-63454: Standardwert für ein Dropdown-Menü und Attribute mit Mehrfachauswahl werden nicht ordnungsgemäß in der Datenbank gespeichert'
description: Wenden Sie den Patch ACSD-63454 an, um das Adobe Commerce-Problem zu beheben, bei dem der Standardwert für ein Dropdown-Attribut und ein Attribut mit Mehrfachauswahl nicht ordnungsgemäß in der Datenbank gespeichert wird.
feature: Attributes, Products
role: Admin, Developer
exl-id: fa79a3bb-e615-44cb-8d84-da892f924fd0
source-git-commit: cb73a5a346ec0e8acd59accf73605e25ef35c3ca
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-63454: Standardwert für ein [!UICONTROL Dropdown] und [!UICONTROL Multiple Select] Attribute wird nicht ordnungsgemäß in der Datenbank gespeichert

Mit dem Patch ACSD-63454 wird das Problem behoben, dass der Standardwert für ein [!UICONTROL Dropdown] und [!UICONTROL Multiple Select] Attribute nicht ordnungsgemäß in der Datenbank gespeichert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 installiert ist. Die Patch-ID ist ACSD-63454. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Standardwert für [!UICONTROL Dropdown]- und [!UICONTROL Multiple Select]-Attribute wird nicht korrekt in der Datenbank gespeichert. Anstatt den Standardwert zu aktualisieren, wird der neue Wert durch ein Komma getrennt an den alten Wert angehängt.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim -Backend an und gehen Sie zu **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Product]**.
1. Klicken Sie auf **[!UICONTROL Add New Attribute]**.
1. Legen Sie auf der Registerkarte **[!UICONTROL Properties]** Folgendes fest:
   * **[!UICONTROL Default Label]**: *test*
   * **[!UICONTROL Catalog Input Type for Store Owner]**: *[!UICONTROL Multiple Select]*
   * **[!UICONTROL Manage Options]**: Fügen Sie zwei Optionen hinzu, ohne **[!UICONTROL Is Default]** auszuwählen.
1. Klicken Sie auf **[!UICONTROL Save Attribute]**.
1. Überprüfen Sie in der Datenbank, ob die `default_value` leer ist.

   `select attribute_code, default_value from eav_attribute where attribute_code = 'test';`

1. Gehen Sie zurück und legen Sie eine der beiden Optionen wie **[!UICONTROL Is Default]** fest.
1. Überprüfen Sie erneut die Datenbank, um sicherzustellen, dass `default_value` jetzt die ausgewählte Option-ID enthält.
1. Gehen Sie zurück und ändern Sie die Standardoption, indem Sie die andere Option auswählen.

<u>Erwartete Ergebnisse</u>:

Der neue Standardwert sollte den alten Wert in der Datenbank ersetzen.

<u>Tatsächliche Ergebnisse</u>:

Anstatt den Standardwert durch den neuen zu ersetzen, fügt es den neuen Wert durch ein Komma getrennt an den alten Wert an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
