---
title: 'ACSD-65913: [!DNL OpenSearch] Löst eine Illegal_Argument_Exception für Kategorien aus, für die Produkte denselben Preis haben'
description: Wenden Sie den Patch ACSD-65913 an, um das Adobe Commerce-Problem zu beheben, bei dem  [!DNL Opensearch] eine Illegal_Argument_Exception (“[from]-Parameter darf nicht negativ sein„) in den Kategorien auslöst, die alle Produkte mit demselben Preis enthalten.
feature: Search
role: Admin, Developer
type: Troubleshooting
exl-id: 984db32e-1a0d-4e0a-a83b-7fe909226ed3
source-git-commit: e24b62305ef97c5fff13582b4bb68f622dffb6d3
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-65913: [!DNL OpenSearch] gibt eine `illegal_argument_exception` für Kategorien mit Produkten, die denselben Preis haben

Mit dem Patch ACSD-65913 wird das Problem behoben, dass [!DNL OpenSearch] eine `illegal_argument_exception` für Kategorien mit Produkten desselben Preises ausgelöst haben. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 installiert ist. Die Patch-ID ist ACSD-65913. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL OpenSearch] löst beim Laden von Kategorien, in `illegal_argument_exception` alle Produkte denselben Preis hatten, einen *[aus] (Parameter darf nicht negativ sein*.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie [!DNL OpenSearch] Version 2.19.1 und legen Sie sie als Standard-Suchmaschine fest.
1. Konfigurieren Sie das **[!UICONTROL Price]** Produktattribut so, dass es in der mehrschichtigen Navigation sichtbar ist:
   1. **[!UICONTROL Visible in Advanced Search]**: *Ja*
   1. **[!UICONTROL Comparable on Storefront]**: *Ja*
   1. **[!UICONTROL Use in Layered Navigation]**: *Filterbar (mit Ergebnissen)*
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Layered Navigation]**. Setzen Sie **[!UICONTROL Price Navigation Step Calculation]** auf *Automatisch (gleicht die Produktzahl an)*.
1. Erstellen Sie eine Kategorie mit sechs Produkten, die alle den gleichen Preis haben:
   1. Artikelnummer: product_super_0-1-1-1, Preis: $150
   1. Artikelnummer: product_super_0-1-1, Preis: $48
   1. Artikelnummer: product_super_0-1, Preis: $48
   1. Artikelnummer: product_super_0, Preis: $48
   1. Artikelnummer: product_super_0-1-1-1-1-1-1-1-1-1-1-1-1-1-1-1-1, Preis: $48
   1. Artikelnummer: product_super_0-1-1-1-1-1-1-1-1-1-1-1-1-1, Preis: $48
1. Führen Sie den folgenden Befehl aus:
   `bin/magento indexer:reindex`
1. Öffnen Sie die Kategorieseite. Es wird ein Fehler angezeigt:
   *[von] Parameter darf nicht negativ sein, gefunden [-1]*

<u>Erwartete Ergebnisse</u>:

[!DNL OpenSearch] sollten keine `illegal_argument_exception` auslösen, wenn alle Produkte in einer Kategorie denselben Preis haben.

<u>Tatsächliche Ergebnisse</u>:

* [!DNL OpenSearch] löst einen `illegal_argument_exception` mit der Nachricht aus:
  *[von] Parameter darf nicht negativ sein, gefunden [-1]*

* Die `var/log/exception.log` enthält:

  ```
  [2025-05-14T22:39:33.595272+00:00] report.CRITICAL: [!DNL OpenSearch]\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"}],"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"},"status":400}
  ```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
