---
title: 'ACSD-66049: Nicht-englische Storefronts zeigen aufgrund der ICU-Bibliotheksversion falsche Preise an'
description: Wenden Sie den Patch ACSD-66049 an, um das Adobe Commerce-Problem zu beheben, bei dem nicht englische Storefronts falsche Preise anzeigen, da die Versionen der ICU-Bibliothek in älteren PHP-Umgebungen (Versionen 63.1 bis 74.1) nicht übereinstimmen.
feature: Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 39e0b972dfa41f74f3c19e61d8fc1188d5c93f7c
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# ACSD-66049: Nicht-englische Storefronts zeigen aufgrund der ICU-Bibliotheksversion falsche Preise an

Der Patch ACSD-66049 behebt das Problem, dass nicht-englische Storefronts aufgrund von Inkompatibilität der ICU-Bibliotheksversionen in älteren PHP-Umgebungen (Versionen 63.1 bis 74.1) falsche Preise anzeigen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 installiert ist. Die Patch-ID ist ACSD-66049. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3 - 2.4.5-p13, 2.4.7 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nicht-englische Storefronts zeigen falsche Preise an, wenn ältere PHP ICU-Bibliotheksversionen (63.1 bis 74.1) verwendet werden.

<u>Schritte zur Reproduktion</u>:

1. ICU-Version überprüfen:
   * Stellen Sie über SSH eine Verbindung mit dem Server her und führen Sie den folgenden Befehl aus: `php -a`
   * Geben Sie bei der Eingabeaufforderung Folgendes ein: `echo INTL_ICU_VERSION;`
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale]** > **[!UICONTROL Locale Options]**. **[!UICONTROL Configure Locale]** = *[UICONTOL Hebräisch (Israel)]*.
1. Produkt mit Preis = 100 erstellen.
1. Sehen Sie sich die Produktseite in der Storefront an.

<u>Erwartete Ergebnisse</u>:

Der angezeigte Preis ist nicht 0.

<u>Tatsächliche Ergebnisse</u>:

Nachdem er kurz als 100 angezeigt wurde, wird der Preis sofort auf 0 aktualisiert.
(Dieses Problem betrifft die PHP ICU-Bibliotheksversionen 63.1 bis 74.1.)

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
