---
title: "ACSD-61553: [!UICONTROL Cart Price Rule] wird falsch berechnet, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden."
description: Wenden Sie den Patch ACSD-61553 an, um das Adobe Commerce-Problem zu beheben, bei dem der [!UICONTROL Cart Price Rule] falsch berechnet wird, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden.
feature: Shopping Cart, Price Rules
role: Admin, Developer
source-git-commit: 299cdaaeb1a97697125cd990a9387d5245226f1d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-61553: [!UICONTROL Cart Price Rule] wird falsch berechnet, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden

Der Patch ACSD-61553 behebt das Problem, dass der [!UICONTROL Cart Price Rule] falsch berechnet wird, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.53 installiert ist. Die Patch-ID ist ACSD-61553. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!UICONTROL Cart Price Rule] wird falsch berechnet, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt mit einem Preis von 9.000 $.
1. Erstellen Sie eine [!UICONTROL Cart Price Rule]: Regel A mit einem festen Rabatt von 700 USD ohne Bedingungen und ohne Verwerfen nachfolgender Regeln.
1. Erstellen Sie eine weitere [!UICONTROL Cart Price Rule]: Regel B mit einem festen Rabatt von 1000 USD ohne Bedingungen und ohne die nachfolgenden Regeln zu verwerfen.
1. Das Produkt mit der Menge 13 zum Warenkorb hinzufügen.
1. Aktualisieren Sie die Regeln mit einem der folgenden Szenarien:

   Szenario 01

       Regel A
       Priorität: 1
       Maximaler Qty-Rabatt wird angewendet auf: 1
       
       Regel B
       Priorität: 0
       Maximaler Qty-Rabatt wird angewendet auf: 0
   
   Szenario 02

       Regel A
       Priorität: 0
       Maximaler Qty-Rabatt wird angewendet auf: 0
       
       Regel B
       Priorität: 1
       Maximaler Qty-Rabatt wird angewendet auf: 1
   
   Szenario 03

       Regel A
       Priorität: 0
       Maximaler Qty-Rabatt wird angewendet auf: 0
       
       Regel B
       Priorität: 0
       Maximaler Qty-Rabatt wird angewendet auf: 1
   
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Update Shopping Cart]** , um die Rabatte neu zu berechnen.

<u>Erwartete Ergebnisse</u>:

Für verschiedene Szenarien wird der folgende Gesamtrabatt angezeigt:

    Szenario 01: $13,700
    Szenario 02: $10,100
    Szenario 03: $10,100

<u>Tatsächliche Ergebnisse</u>:

In allen drei Szenarien beträgt der Gesamtrabatt 9.000 USD.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.