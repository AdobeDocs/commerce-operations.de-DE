---
title: 'ACSD-61799: Falsche Berechnung des Gesamtrabatts mit mehreren Regeln für den festen Rabatt auf das Angebot angewendet'
description: Wenden Sie den Patch ACSD-61799 an, um das Adobe Commerce-Problem zu beheben, bei dem der Gesamtrabatt falsch berechnet wird, wenn mehrere Warenkorbregeln mit festen Rabatten auf das Angebot angewendet werden.
feature: Price Rules
role: Admin, Developer
exl-id: a87ec1cd-f141-43b9-bde1-eca354c12d4e
source-git-commit: 737204ae7418f49fdebfffbf351304796e9f5eb0
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-61799: Falsche Berechnung des Gesamtrabatts mit mehreren Regeln für den festen Rabatt auf das Angebot angewendet

Der Patch ACSD-61799 löst/behebt das Problem, dass der Gesamtrabatt falsch berechnet wird, wenn mehrere Warenkorbregeln mit festen Rabatten auf das Angebot angewendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61799. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Gesamtrabatt wird falsch berechnet, wenn mehrere Warenkorbregeln mit *[!UICONTROL Fixed amount discount for the whole cart]* auf einen Warenkorb angewendet werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie vier Produkte mit einem Preis von $1000.
1. Erstellen Sie drei Warenkorb-Preisregeln ohne Bedingungen, die einen Rabatt von 100 USD für den gesamten Warenkorb gewähren.
1. Erstellen Sie eine weitere Warenkorb-Preisregel, die einen Rabatt von 100 USD für den gesamten Warenkorb gewährt, mit einer Bedingung, die die Anwendung der Regel verhindert.
1. Deaktivieren Sie die Regel.
1. Fügen Sie drei Produkte zum Warenkorb hinzu und beachten Sie den Rabatt im Warenkorb.
1. Fügen Sie zusätzliche Produkte zum Warenkorb hinzu und beachten Sie den Rabatt im Warenkorb.
1. Aktivieren Sie die deaktivierte Warenkorb-Preisregel.
1. Aktualisieren Sie die Warenkorbseite und beachten Sie den Rabatt im Warenkorb.

<u>Erwartete Ergebnisse</u>:

1. Durch das Hinzufügen zusätzlicher Produkte zum Warenkorb wird der Rabattbetrag nicht geändert.
1. Wenn Sie die Preisregel für den Warenkorb mit einer Bedingung aktivieren, die nicht zutrifft, ändert sich der Rabattbetrag nicht.

<u>Tatsächliche Ergebnisse</u>:

1. Wenn Sie dem Warenkorb zusätzliche Produkte hinzufügen, ändert sich der Rabattbetrag.
1. Wenn Sie die Preisregel für den Warenkorb mit einer Bedingung aktivieren, die nicht angewendet wird, ändert sich der Rabattbetrag.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
