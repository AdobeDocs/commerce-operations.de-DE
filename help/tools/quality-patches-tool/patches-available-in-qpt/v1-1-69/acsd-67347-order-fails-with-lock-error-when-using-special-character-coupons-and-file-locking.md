---
title: 'ACSD-67347: Bestellung schlägt fehl mit der Fehlermeldung „Sperrung kann nicht erworben werden“ bei Verwendung von Gutscheincodes'
description: Wenden Sie den ACSD-67347 Patch auf das Adobe Commerce-Problem an, bei dem Bestellungen mit dem Fehler „Keine Sperre möglich“ fehlschlagen, wenn Couponcodes Sonderzeichen enthalten (z. B. BIT/123456) und die Dateisperre aktiviert ist.
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1a48428efbb022b53320370f68691eaed44809b3
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-67347: Bestellung schlägt fehl mit *Sperrung nicht möglich* Fehler bei Verwendung von Gutscheincodes

Der Patch ACSD-67347 behebt das Problem, dass Bestellungen mit dem Fehler *Keine Sperre erhalten* fehlschlagen, wenn Couponcodes Sonderzeichen enthalten (z. B. BIT/123456) und die Dateisperre aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist ACSD-67347. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p12

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p11 - 2.4.5-p13

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bestellungen schlagen mit dem Fehler *Sperrung nicht möglich* fehl, wenn Coupons mit Sonderzeichen verwendet werden und die Dateisperrung aktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie 2.4-develop.
1. Legen Sie die Dateisperre-Konfiguration in der `env.php` fest:

   ```
   'lock' => [
           'provider' => 'file',
           'config' => [
               'path' => '/Users/awijesooriya/sites/acsd15194dev/locks'
           ]
       ],
   ```

1. Erstellen Sie eine Warenkorbregel mit einem Coupon im Coupon-Code-Format: *BIT/123456*.
1. Erstellen Sie ein einfaches Produkt.
1. Fügen Sie das Produkt zum Warenkorb hinzu und wenden Sie den Gutscheincode an.
1. Fahren Sie mit der Kasse fort und geben Sie die Bestellung auf.

<u>Erwartete Ergebnisse</u>:

Die Bestellungen wurden erfolgreich aufgegeben, da es keine Einschränkungen bei der Erstellung von Gutscheincodes gibt.

<u>Tatsächliche Ergebnisse</u>:

Bestellung nicht möglich. Der folgende Fehler wird angezeigt: *Sperre kann nicht abgerufen werden.*

```
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
