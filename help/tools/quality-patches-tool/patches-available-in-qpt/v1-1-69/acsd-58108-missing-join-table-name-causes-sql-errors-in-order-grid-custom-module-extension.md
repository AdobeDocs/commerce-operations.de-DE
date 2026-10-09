---
title: 'ACSD-58108: SQL-Fehler treten aufgrund eines fehlenden Join-Tabellennamen im Reihenfolgen-Raster in der benutzerdefinierten Modulerweiterung auf'
description: Wenden Sie den Patch ACSD-58108 an, um das Adobe Commerce-Problem zu beheben, bei dem ein fehlender Join-Tabellenname in der benutzerdefinierten Modulerweiterung des Reihenfolgenrasters beim Filtern bestimmter Spalten zu SQL-Fehlern führt.
feature: Orders, System
role: Admin, Developer
type: Troubleshooting
exl-id: 1195e1c3-575c-48d6-8a10-c300f9bbb84a
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%
---
# ACSD-58108: SQL-Fehler treten aufgrund eines fehlenden Join-Tabellennamen im Reihenfolgen-Raster in der benutzerdefinierten Modulerweiterung auf

Der Patch ACSD-58108 behebt das Problem, dass ein fehlender Join-Tabellenname in der benutzerdefinierten Modulerweiterung des Reihenfolgen-Rasters beim Filtern bestimmter Spalten zu SQL-Fehlern führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist ACSD-58108. Dieses Problem wird voraussichtlich in Adobe Commerce 2.5.0 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der fehlende Join-Tabellenname in der ursprünglichen Abruftabelle führt zu SQL-Fehlern im Reihenfolgen-Raster bei Verwendung einer benutzerdefinierten Modulerweiterung. Dieses Problem tritt auf, weil die `addFilterToMap`-Funktion für bestimmte Spalten nach dem Verbinden mit der **[!UICONTROL sales_order_item]** nicht funktioniert, was zu Fehlern beim Filtern führt.

<u>Schritte zur Reproduktion</u>:

&#x200B;01. Installieren Sie eine 2.4-develop-Instanz.
&#x200B;02. Erstellen Sie eine neue Bestellung.
&#x200B;03. Installieren Sie ein benutzerdefiniertes Modul mit einer SQL-Erweiterung.
&#x200B;04. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
&#x200B;05. Wenden Sie den **[!UICONTROL Purchase Date]** an und warten Sie auf das Ergebnis.
&#x200B;06. **[!UICONTROL Product SKU]** anwenden.

<u>Erwartete Ergebnisse</u>:

Das Filtern von Bestellungen im Bestellraster funktioniert fehlerfrei.

<u>Tatsächliche Ergebnisse</u>:

Beim Anwenden von Filtern im Ordnungsraster tritt ein Fehler auf.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
