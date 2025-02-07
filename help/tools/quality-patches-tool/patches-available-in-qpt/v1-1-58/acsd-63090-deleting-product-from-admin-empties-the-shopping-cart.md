---
title: 'ACSD-63090: Beim Löschen eines Produkts aus der Administratorliste wird der Warenkorb geleert'
description: Wenden Sie den Patch ACSD-63090 an, um das Adobe Commerce-Problem zu beheben, bei dem die Artikel im Warenkorb eines Kunden verschwanden, weil ein Produkt gelöscht wurde, nachdem es zum Warenkorb hinzugefügt wurde.
feature: Shopping Cart, Quotes
role: Admin, Developer
source-git-commit: 513993f0c4bd97047ad128a25a4b2a6b3eebd82b
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63090: Beim Löschen eines Produkts aus der Administratorliste wird der Warenkorb geleert

Mit dem Patch ACSD-63090 wird das Problem behoben, dass die Artikel im Warenkorb eines Kunden verschwanden, weil ein Produkt aus Admin gelöscht wurde, nachdem es zum Warenkorb hinzugefügt wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 installiert ist. Die Patch-ID ist ACSD-63090. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Artikel im Warenkorb verschwinden, wenn ein Produkt gelöscht wird, nachdem es zum Warenkorb hinzugefügt wurde.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit zwei untergeordneten Produkten.
1. Melden Sie sich als registrierter Kunde an.
1. Fügen Sie beide untergeordneten Produkte zum Warenkorb hinzu.
1. Melden Sie sich vom Konto ab.
1. Löschen Sie eines der untergeordneten Produkte aus dem Katalog.
1. Aktualisieren Sie den Preis des anderen untergeordneten Produkts mithilfe der -API.

<u>Erwartete Ergebnisse</u>:

Das verbleibende Produkt wird im Warenkorb angezeigt und das vorhandene Angebot wird in der `quote` Datenbanktabelle aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

* Der Miniwagen ist leer.
* In der `quote`-Datenbanktabelle wird ein neuer Anführungseintrag generiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
