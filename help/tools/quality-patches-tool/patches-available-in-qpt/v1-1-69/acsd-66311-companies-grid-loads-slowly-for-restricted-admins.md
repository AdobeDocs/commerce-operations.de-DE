---
title: 'ACSD-66311: Das Firmen-Raster wird für Administratoren mit eingeschränkter Zugriffsberechtigung langsam geladen'
description: Wenden Sie den Patch ACSD-66311 an, um das Adobe Commerce-Problem zu beheben, bei dem das Unternehmensraster für Admin-Benutzer mit eingeschränktem Website-Zugriff langsam geladen wird.
role: Admin, Developer
feature: B2B
type: Troubleshooting
exl-id: e470078b-dd10-4b0b-a489-bc88f025fded
source-git-commit: 3337907b1893260d6cb18b1c4fbf45dfa1f3d6d5
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 2%

---

# ACSD-66311: Das Firmen-Raster wird für Administratoren mit eingeschränkter Zugriffsberechtigung langsam geladen

Mit dem Patch ACSD-66311 wird das Problem behoben, dass das Unternehmensraster für Admin-Benutzer mit eingeschränktem Website-Zugriff langsam geladen wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist ACSD-66311. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p4 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Firmen-Raster wird für Admin-Benutzer mit eingeschränktem Website-Zugriff langsam geladen.

<u>Schritte zur Reproduktion</u>:

1. Installieren von Adobe Commerce mit **[!UICONTROL B2B features]**.
1. Erstellen Sie zwei zusätzliche Websites (zusätzlich zur Haupt-Website) mit Stores/Ansichten:
   * Haupt-Website (wird während der Installation erstellt)
   * Website 2 → Store 2 → StoreView 2
   * Website 3 → Store 3 → StoreView 3
1. Erstellen Sie die **[!UICONTROL Admins in Scope]** Benutzerrolle:
   * Umfang: nur zwei Geschäfte: *Haupt-Website* + *Website 3/Store 3*.
   * Ressourcen: nur *Dashboard* + *Firmen*.
1. Erstellen Sie einen Admin-Benutzer mit einer Rolle **[!UICONTROL Admins in Scope]**, z. B **„adminscope**.
1. Generieren spezifischer verteilter Kunden- und Unternehmensdaten:
   1. **Kunden, die Websites zugewiesen sind**

      | Website-ID | Anzahl der Kunden |
      |------------|---------------------|
      | 1 | 600.000 |
      | 2 | 1.500 |
      | 3 | 500 |

   1. Führen Sie die folgende Abfrage aus, um die Verteilung zu überprüfen:

      ```
           SELECT website_id, COUNT(*) 
           FROM customer_entity 
           GROUP BY website_id; 
      ```

   1. **Kunden, die Firmen zugewiesen sind**

      | Anzahl der Kunden | Anzahl der Unternehmen |
      |---------------------|---------------------|
      | 1 | 4.500 |
      | 2 | ~1.000 |
      | ~595 K | 1 |

   1. Führen Sie die folgende Abfrage aus, um die Verteilung zu überprüfen:

      ```
            SELECT customer_count, COUNT(*) AS number_of_companies
            FROM (
              SELECT company_id, COUNT(customer_id) AS customer_count
              FROM company_advanced_customer_entity
              GROUP BY company_id
            ) AS subquery
            GROUP BY customer_count
            ORDER BY customer_count; 
      ```

1. Indizieren Sie alle Daten neu, um Einträge in der **customer_grid_flat** zu generieren.
1. Melden Sie sich als **adminscope** an.
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL Companies]**.

<u>Erwartete Ergebnisse</u>:

Die Seite wird in weniger als 1 Sekunde geladen.

<u>Tatsächliche Ergebnisse</u>:

Das Laden der Seite dauert mehr als 14 Minuten.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
