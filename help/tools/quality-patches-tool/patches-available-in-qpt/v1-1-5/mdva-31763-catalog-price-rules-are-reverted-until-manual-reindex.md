---
title: 'MDVA-31763: Katalogpreisregeln werden bis zur manuellen Neuindizierung zurückgesetzt'
description: Der Patch MDVA-31763 löst das Problem, dass Katalogpreisregeln bis zu einer manuellen Neuindizierung zurückgesetzt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-31763. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Catalog Management, Orders, Price Rules
role: Admin
exl-id: 1d144bfc-c26b-43d0-a80c-26a9c2d8ef32
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-31763: Katalogpreisregeln werden bis zur manuellen Neuindizierung zurückgesetzt

Der Patch MDVA-31763 löst das Problem, dass Katalogpreisregeln bis zu einer manuellen Neuindizierung zurückgesetzt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-31763. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn `catalogrule_product` partieller Indexer für konfigurierbare Produkte ausgeführt wird, werden Katalogregeln ausgeblendet.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin-Backend an.
1. Wechseln Sie zu **Stores** > **Attribute** > **Produkt** und suchen Sie nach dem Attribut &quot;Hersteller&quot;.
   * Fügen Sie einige Optionen hinzu und setzen Sie &quot;Use for Promo Rule Conditions&quot;auf *Yes*.
1. Wechseln Sie zu **Stores** > **Attribute** > **Attributsätze**.
   * Wählen Sie den Standard-Attributsatz aus und fügen Sie ihm das Attribut &quot;manufacturer&quot;hinzu.
1. Erstellen Sie ein konfigurierbares Produkt mit mehreren Varianten.
1. Legen Sie den Attributwert &quot;manufacturer&quot;für das zuvor erstellte konfigurierbare Produkt fest.
1. Erstellen von Katalogregeln:
   * Aktiv = Ja
   * Websites = Hauptseite
   * Kundengruppen = NICHT ANGEMELDET
   * Bedingungen: manufacturer = \&lt;ausgewählter Wert für konfigurierbares Produkt>
   * Aktionen: Alle Rabatte
1. Führen Sie einen vollständigen Index durch.
1. Überprüfen Sie den Produktpreis auf PDP und stellen Sie sicher, dass der Preis korrekt ist.
1. Aktualisieren Sie das Attribut &quot;Gewichtung&quot;des erstellten konfigurierbaren Produkts.
1. Überprüfen Sie den Produktpreis auf PDP.

<u>Erwartete Ergebnisse</u>:

Die für konfigurierbare Produkte festgelegten Katalogpreisregeln werden bei einer partiellen Neuindizierung nicht entfernt.

<u>Tatsächliche Ergebnisse</u>:

Die für konfigurierbare Produkte festgelegten Katalogpreisregeln werden bei einer partiellen Neuindizierung nicht mehr angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
