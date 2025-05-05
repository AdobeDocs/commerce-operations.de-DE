---
title: 'ACSD-63469: Warenkorb-Rabatte mit festem Betrag werden mit mehreren Regeln nicht korrekt angewendet'
description: Wenden Sie den Patch ACSD-63469 an, um das Adobe Commerce-Problem zu beheben, bei dem Pauschalrabatte für den gesamten Warenkorb nicht richtig angewendet werden, wenn mehr als eine Regel angewendet wird.
feature: Price Rules
role: Admin, Developer
source-git-commit: 3699a9f64198558fcf1ffe53753f035d22c2d301
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---


# ACSD-63469: Warenkorb-Rabatte mit festem Betrag werden mit mehreren Regeln nicht korrekt angewendet

Der Patch ACSD-63469 behebt das Problem, dass Festbetragsrabatte für den gesamten Warenkorb nicht richtig gelten, wenn mehr als eine Regel angewendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 installiert ist. Die Patch-ID ist ACSD-63469. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn mehrere **[!UICONTROL Fixed amount discount for whole cart]** gleichzeitig angewendet werden und die Produkte Rabatte oder Sonderpreise haben, wird der Rabattwert falsch berechnet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Produkte zu einem Preis von 850 und 85 Dollar und setzen Sie ihre Sonderpreise auf 765 bzw. 68 Dollar fest.
1. Erstellen Sie zwei **[!UICONTROL Cart Price Rules]** wie folgt:
   * Artikel 1
      * **[!UICONTROL Conditions]**: Setzen Sie für das Produkt $850 *Qty* auf *gleich oder größer als 2*
      * **[!UICONTROL Actions]**: **[!UICONTROL Fixed amount discount for whole cart]** von *$153 anwenden*
   * Regel 2
      * **[!UICONTROL Conditions]**: Für das Produkt $85 setzen Sie *Qty* auf *gleich oder größer als 2*
      * **[!UICONTROL Actions]**: **[!UICONTROL Fixed amount discount for whole cart]** von *$14 anwenden*
1. Fügen Sie beide Produkte mit jeweils einer Menge von 2 in den Warenkorb.

<u>Erwartete Ergebnisse</u>:

Der im Warenkorb angewendete Rabatt beträgt $167.

<u>Tatsächliche Ergebnisse</u>:

Der im Warenkorb angewendete Rabatt beträgt 41 USD.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Zusätzliche Schritte nach der Patch-Installation erforderlich

(Dieser Abschnitt ist optional. Nach der Anwendung des Patches sind möglicherweise einige Schritte erforderlich, um das Problem zu beheben.) 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.

