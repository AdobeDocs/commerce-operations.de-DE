---
title: 'ACSD-62793: Datetime-Attribute in Exporten ohne Zeitkomponente. Wenn **[!UICONTROL Fields Enclosure]** aktiviert ist, werden Attributwerte in doppelte Anführungszeichen gesetzt'
description: Wenden Sie den ACSD-62793-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Datums-/Uhrzeitattribute in exportierten Daten nicht in der Zeitkomponente enthalten sind. Wenn **[!UICONTROL Fields Enclosure]** aktiviert ist, werden Attributwerte in der Spalte * additional_attributes* außerdem in doppelte Anführungszeichen gesetzt.
feature: Attributes, Data Import/Export, Catalog Service
role: Admin, Developer
exl-id: 340dcc84-dcb8-40ed-b2ab-2d950d1dd1ca
source-git-commit: 96ba8b422524eb06989061f2d40e39ea88b71dca
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-62793: Datetime-Attribute in Exporten ohne Zeitkomponente. Wenn diese Option aktiviert **[!UICONTROL Fields Enclosure]**, werden außerdem Attributwerte in doppelte Anführungszeichen gesetzt

Mit dem Patch ACSD-62793 wird das Problem behoben, dass in exportierten Daten Datums-/Uhrzeitattributen die Zeitkomponente fehlt. Wenn **[!UICONTROL Fields Enclosure]** aktiviert ist, werden Attributwerte in der Spalte *additional_attributes* in doppelte Anführungszeichen gesetzt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-62793. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Datetime-Attribute enthalten in exportierten Daten nicht die Zeitkomponente. Wenn **[!UICONTROL Fields Enclosure]** aktiviert ist, werden Attributwerte in der Spalte *additional_attributes* in doppelte Anführungszeichen gesetzt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produktattribut mit **[!UICONTROL Catalog Input Type for Store Owner]** = **[!UICONTROL Date and Time]**.
1. Weisen Sie das Attribut dem **[!UICONTROL Default]** Attributsatz zu.
1. Erstellen Sie ein einfaches Produkt mit einem Datums- und Uhrzeitwert für das neue Attribut.
1. Exportieren Sie das Produkt in eine CSV-Datei über **[!UICONTROL System]** > *Datenübertragung* > **[!UICONTROL Export]**.
1. Überprüfen Sie den Attributwert in der Spalte *additional_attributes*. Sie hat nur den Datumsteil, aber keine Zeit.
1. Aktualisieren Sie den Attributwert so, dass er die Zeit verwendet, z. B. „08/10/22, 15:20 Uhr“.
1. Importieren Sie die CSV-Datei.
1. Überprüfen Sie die *CATALOG_PRODUCT_ENTITY_DATETIME*-Tabelle.

<u>Erwartete Ergebnisse</u>:

Datum und Uhrzeit werden ordnungsgemäß exportiert und importiert.

<u>Tatsächliche Ergebnisse</u>:

Nur der Datumsteil wird exportiert und importiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
