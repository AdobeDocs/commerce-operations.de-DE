---
title: 'ACSD-61895: Abfrage [!DNL GraphQL] Kategorien schlägt für privaten freigegebenen Katalog mit eingeschränkter Ansicht fehl'
description: Wenden Sie den Patch ACSD-61895 an, um das Adobe Commerce-Problem zu beheben, bei dem [!DNL GraphQL] Antworten für Gastkunden (unter Verwendung eines öffentlichen freigegebenen Katalogs mit allen zulässigen Kategorien) keine Kategorien zurückgaben, wenn ein privater freigegebener Katalog mit Einschränkungen für dieselben Kategorien erstellt wurde.
feature: Categories, GraphQL, Roles/Permissions
role: Admin, Developer
exl-id: ef986fa6-e8bc-4322-80f2-fa0c5d5e8d40
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
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
source-wordcount: '564'
ht-degree: 0%
---
# ACSD-61895: [!DNL GraphQL] `categories` Abfrage schlägt für privaten freigegebenen Katalog mit eingeschränkter Ansicht fehl

Der Patch ACSD-61895 behebt das Problem, dass [!DNL GraphQL] Antworten für Gastkunden (unter Verwendung eines öffentlichen freigegebenen Katalogs mit allen zulässigen Kategorien) keine Kategorien zurückgaben, wenn ein privater freigegebener Katalog mit Einschränkungen für dieselben Kategorien erstellt wurde.

Nach der Behebung werden alle Kategorien mit Berechtigungen (öffentlicher freigegebener Katalog) für Gastbenutzer zurückgegeben, auch wenn die Stammkategorie keine Berechtigung im Bereich eines privaten freigegebenen Katalogs hat.

Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-61895. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL GraphQL]-Antworten für Gastkunden (die einen öffentlichen freigegebenen Katalog mit allen zulässigen Kategorien verwenden) geben keine Kategorien zurück, wenn für dieselben Kategorien ein privater freigegebener Katalog mit Einschränkungen erstellt wird.

<u>Schritte zur Reproduktion</u>:

1. Installieren von Adobe Commerce mit B2B- und Beispieldaten.
1. Stellen Sie sicher, dass B2B-Funktionen aktiviert sind.
1. Erstellen Sie zwei freigegebene Kataloge: einen öffentlichen und einen privaten.

   * Öffentlicher freigegebener Katalog:

     * Weisen Sie alle Kategorien dem öffentlichen Katalog zu.

   * Privater freigegebener Katalog:

     * Weisen Sie nur die `Gear` Kategorie und ihre untergeordneten Kategorien dem privaten Katalog zu.
     * Weisen Sie den privaten Katalog einer Testfirma zu.

1. Einen Unternehmensbenutzer erstellen:

   * Erstellen Sie einen Benutzer, der mit der Testfirma verknüpft ist, die mit dem privaten freigegebenen Katalog verknüpft ist.
   * Stellen Sie sicher, dass der Benutzer nur auf die `Gear` Kategorie und ihre untergeordneten Kategorien im Frontend zugreifen kann, wenn er angemeldet ist.

1. Abfragen von Kategorien über API:

   * Verwenden Sie den API-Client, um die folgende [!DNL GraphQL]-Abfrage ohne Kunden-Token auszuführen:

   ```graphql
   query Categories { 
       categories { 
           items { 
               children_count 
               children { 
                   uid 
                   name 
                   children_count 
                   children { 
                   uid 
                   name 
                   } 
               } 
           } 
       } 
   }
   ```

1. Beobachten Sie die Antwort und überprüfen Sie, ob die `Gear` Kategorie und andere Kategorien zurückgegeben werden.
1. Abfragen von Kategorien mit einem Kunden-Token:

   * Melden Sie sich als Benutzer der Testfirma an.
   * Führen Sie dieselbe [!DNL GraphQL] Kategorieabfrage aus, schließen Sie jedoch das Kunden-Token für den angemeldeten Benutzer ein.
   * Beobachten Sie die Antwort und überprüfen Sie, ob nur die `Gear` Kategorie und ihre untergeordneten Kategorien zurückgegeben werden.


<u>Erwartete Ergebnisse</u>:

Bei der Abfrage als Benutzer eines Gastunternehmens sollten alle Kategorien zurückgegeben werden (erwartungsgemäß).

<u>Tatsächliche Ergebnisse</u>:

Die Antwort aus der `categories` Abfrage zeigt keine Kategorien an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
