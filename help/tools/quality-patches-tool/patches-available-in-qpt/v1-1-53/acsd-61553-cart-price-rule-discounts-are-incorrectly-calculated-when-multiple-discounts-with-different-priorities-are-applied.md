---
title: 'ACSD-61553: [!UICONTROL Cart Price Rule] wird falsch berechnet, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden'
description: Wenden Sie den Patch ACSD-61553 an, um das Adobe Commerce-Problem zu beheben, bei dem die [!UICONTROL Cart Price Rule] falsch berechnet wird, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
source-git-commit: b182fc0cd2f00f36138675277ac1de8a7179135a
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-61553: [!UICONTROL Cart Price Rule] wird falsch berechnet, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden

Mit dem Patch ACSD-61553 wird das Problem behoben, dass die [!UICONTROL Cart Price Rule] falsch berechnet wird, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.53 installiert ist. Die Patch-ID ist ACSD-61553. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!UICONTROL Cart Price Rule] wird falsch berechnet, wenn mehrere Rabatte mit unterschiedlichen Prioritäten angewendet werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt mit einem Preis von 9.000 $.
1. Erstellen Sie eine [!UICONTROL Cart Price Rule]: Regel A mit einem festen Rabatt von 700 $ ohne Bedingungen und ohne Verwerfen der nachfolgenden Regeln.
1. Erstellen Sie eine weitere [!UICONTROL Cart Price Rule]: Regel B mit einem festen Rabatt von 1.000 $ ohne Bedingungen und ohne Verwerfen der nachfolgenden Regeln.
1. Fügen Sie das Produkt mit der Menge 13 in den Warenkorb.
1. Aktualisieren Sie die Regeln mit einem der folgenden Szenarien:

   Szenario 01

       Regel A
       Priorität: 1
       Maximaler Mengenrabatt wird angewendet auf: 1
       
       Regel B
       Priorität: 0
       Maximaler Mengenrabatt wird angewendet auf: 0
   
   Szenario 02

       Regel A
       Priorität: 0
       Maximaler Mengenrabatt wird angewendet auf: 0
       
       Regel B
       Priorität: 1
       Maximaler Mengenrabatt wird angewendet auf: 1
   
   Szenario 03

       Regel A
       Priorität: 0
       Maximaler Mengenrabatt wird angewendet auf: 0
       
       Regel B
       Priorität: 0
       Maximaler Mengenrabatt wird angewendet auf: 1
   
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Update Shopping Cart]**, um die Rabatte neu zu berechnen.

<u>Erwartete Ergebnisse</u>:

Der folgende Gesamtrabatt wird für verschiedene Szenarien angezeigt:

    Szenario 01: 13.700 $ 
    Szenario 02: 10.100 $ 
    Szenario 03: 10.100 $

<u>Tatsächliche Ergebnisse</u>:

In allen drei Szenarien beträgt der Gesamtrabatt 9.000 US-Dollar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!DNL Quality Patches Tool].

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
