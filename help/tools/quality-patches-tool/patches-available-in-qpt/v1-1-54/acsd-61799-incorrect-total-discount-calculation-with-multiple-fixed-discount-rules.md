---
title: 'ACSD-61799: Falsche Berechnung des Gesamt-Rabatts mit mehreren auf das Angebot angewendeten Regeln für den festen Rabattkarton'
description: Wenden Sie den Patch ACSD-61799 an, um das Adobe Commerce-Problem zu beheben, bei dem der Gesamtrabatt falsch berechnet wird, wenn mehrere Warenkorbregeln mit festen Rabatten auf das Angebot angewendet werden.
feature: Price Rules
role: Admin, Developer
exl-id: a87ec1cd-f141-43b9-bde1-eca354c12d4e
source-git-commit: 737204ae7418f49fdebfffbf351304796e9f5eb0
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-61799: Falsche Berechnung des Gesamt-Rabatts mit mehreren auf das Angebot angewendeten Regeln für den festen Rabattkarton

Der Patch ACSD-61799 behebt/behebt das Problem, dass der Gesamtrabatt falsch berechnet wird, wenn mehrere Warenkorbregeln mit festen Rabatten auf das Angebot angewendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61799. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Gesamtrabatt wird falsch berechnet, wenn mehrere Warenkorbregeln mit *[!UICONTROL Fixed amount discount for the whole cart]* auf einen Warenkorb angewendet werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie vier Produkte mit einem Preis von 1000 USD.
1. Erstellen Sie drei Preisregeln für den Warenkorb ohne Bedingungen, die einen Rabatt von 100 USD für den gesamten Warenkorb gewähren.
1. Erstellen Sie eine weitere Regel zum Warenkorbpreis, die einen Rabatt von 100 USD für den gesamten Warenkorb gewährt, mit einer Bedingung, die verhindert, dass die Regel angewendet wird.
1. Deaktivieren Sie die Regel.
1. Fügen Sie drei Produkte zum Warenkorb hinzu und beobachten Sie den Rabatt im Warenkorb.
1. Fügen Sie weitere Produkte zum Warenkorb hinzu und beobachten Sie den Rabatt im Warenkorb.
1. Aktivieren Sie die Regel Deaktivierung des Warenkorbpreises.
1. Aktualisieren Sie die Warenkorbseite und beachten Sie den Rabatt im Warenkorb.

<u>Erwartete Ergebnisse</u>:

1. Wenn Sie zusätzliche Produkte zum Warenkorb hinzufügen, ändert sich der Rabatt nicht.
1. Wenn Sie die Preisregel für den Warenkorb mit einer Bedingung aktivieren, die nicht gilt, ändert sich der Rabatt nicht.

<u>Tatsächliche Ergebnisse</u>:

1. Wenn Sie zusätzliche Produkte zum Warenkorb hinzufügen, ändert sich der Rabatt.
1. Wenn Sie die Preisregel für den Warenkorb mit einer Bedingung aktivieren, die nicht angewendet wird, ändert sich der Rabatt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
