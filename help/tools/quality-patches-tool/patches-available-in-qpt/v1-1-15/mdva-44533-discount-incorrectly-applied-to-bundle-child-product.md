---
title: 'MDVA-44533: Rabatt wurde falsch auf gebündeltes untergeordnetes Produkt angewendet'
description: Der Patch MDVA-44533 behebt das Problem, dass ein Rabatt fälschlicherweise auf ein gebündeltes untergeordnetes Produkt angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-44533. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Orders, Personalization, Products
role: Admin
exl-id: 150fe577-a61a-451e-838a-d60be7754bf4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-44533: Rabatt wurde falsch auf gebündeltes untergeordnetes Produkt angewendet

Der Patch MDVA-44533 behebt das Problem, dass ein Rabatt fälschlicherweise auf ein gebündeltes untergeordnetes Produkt angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-44533. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Rabatt wird fälschlicherweise auf ein gebündeltes untergeordnetes Produkt angewendet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt mit einem Preis von 50 $.
1. Erstellen Sie ein gebündeltes Produkt und weisen Sie das einfache Produkt als einzige Option für das gebündelte Produkt zu.
1. Erstellen Sie eine Warenkorb-Preisregel mit:

   * Bedingung: Wenn der Gesamtbetrag größer als 130 $ ist
   * Aktion: Es wird ein Festbetrag-Rabatt von 10 $ angewendet

1. Gehen Sie zur Storefront und fügen Sie das Bundle-Produkt mit der Menge = 1 in den Warenkorb.
1. Gehen Sie zum Warenkorb und überprüfen Sie, ob die Gesamtkosten des Bundle-Produkts 50 $ betragen und der Rabatt nicht zutrifft.
1. Ändern Sie die Menge in 2 und aktualisieren Sie den Warenkorb. Die Gesamtkosten für das gebündelte Produkt sollten jetzt 100 $ betragen.

<u>Erwartete Ergebnisse</u>:

Der Rabatt wird nicht angewendet, da die Zwischensumme 100\$ beträgt, was in der Regelbedingung weniger als 130\$ beträgt.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt wird angewendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
