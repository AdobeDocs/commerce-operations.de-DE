---
title: 'ACSD-65775: Falsche Werte „base_row_total“ und „row_total“ in REST-API-Bestelldetails für mehrere Mengen'
description: Wenden Sie den Patch ACSD-65775 an, um das Adobe Commerce-Problem zu beheben, bei dem die REST-API-Bestelldetails falsche Werte für „base_row_total“ und „row_total“ zurückgeben, wenn mehrere Mengen desselben Artikels bestellt werden.
feature: REST
role: Admin, Developer
type: Troubleshooting
source-git-commit: 23c78abaf28f64baf0e91bcaf89bd0e34b5bf78a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# ACSD-65775: Falsche `base_row_total`- und `row_total`-Werte in REST-API-Bestelldetails für mehrere Mengen

Mit dem Patch ACSD-65775 wird das Problem behoben, dass die Auftragsdetails der REST-API falsche `base_row_total`- und `row_total` zurückgeben, wenn mehrere Mengen desselben Artikels bestellt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 installiert ist. Die Patch-ID ist ACSD-65775. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die `base_row_total` und `row_total` in der Antwort der REST-API zu den Bestelldetails zeigen den Stückpreis anstelle des Gesamtpreises an, wenn mehrere Mengen desselben Artikels bestellt werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei einfache Produkte: simple1 mit einem Preis von $10 und simple2 mit einem Preis von $15.
1. Erstellen Sie ein neues Kundenkonto.
1. Fügen Sie simple1 mit quantity 2 zum Warenkorb und simple2 mit quantity 3.
1. Bestellung über das Kundenkonto aufgeben.
1. Erhalten Sie ein Admin-Token, indem Sie eine POST-Anfrage an `/rest/V1/integration/admin/token` mit der folgenden Payload senden:

   ```
   {
     "username": "admin",
     "password": "password"
   }
   ```

1. Rufen Sie die Bestelldetails über eine GET-Anfrage an `/rest/default/V1/orders/1` ab.

<u>Erwartete Ergebnisse</u>:

`base_row_total` und `row_total` sollten den Gesamtpreis widerspiegeln, der als Menge multipliziert mit dem Artikelpreis berechnet wurde (z. B. 2 × 10 $ = 20 $ für Simple1).

<u>Tatsächliche Ergebnisse</u>:

`base_row_total` und `row_total` geben nur den Stückpreis zurück (z. B. 10 $ für simple1 statt 20 $).

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
