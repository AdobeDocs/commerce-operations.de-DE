---
title: 'ACP2E-3841: Die Warenkorb-Preisregeln für Produkte mit mehreren Versandarten gelten nicht korrekt, wenn Subselect-Bedingungen verwendet werden und der kostenlose Versand aktiviert ist'
description: Wenden Sie den Patch ACP2E-3841 an, um das Adobe Commerce-Problem zu beheben, bei dem die Warenkorbpreisregeln für Produkte mit mehreren Versandarten nicht korrekt angewendet werden, wenn Bedingungen zur Unterauswahl verwendet werden und der kostenlose Versand aktiviert ist.
feature: Shopping Cart, Price Rules
role: Admin, Developer
source-git-commit: 1abb32109d5ca4a90cdd1d210d1fae6a728699fd
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---


# ACP2E-3841: Die Warenkorb-Preisregeln für Produkte mit mehreren Versandarten gelten nicht korrekt, wenn Subselect-Bedingungen verwendet werden und der kostenlose Versand aktiviert ist

Der Patch ACP2E-3841 behebt das Problem, dass die Warenkorbpreisregeln für Produkte mit mehreren Versandarten nicht korrekt angewendet werden, wenn Subselect-Bedingungen verwendet werden und der kostenlose Versand aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 installiert ist. Die Patch-ID lautet ACP2E-3841. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p9

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.7-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Warenkorb-Preisregeln für Produkte mit mehreren Versandarten gelten nicht korrekt, wenn Bedingungen zur Unterauswahl verwendet werden und der kostenlose Versand aktiviert ist.

<u>Voraussetzungen</u>:

**Einstellungen:**
1. **[!UICONTROL Free Shipping]** = *enabled*
1. **[!UICONTROL Minimum Order Amount]** = *99999999*

**Erforderliche Kategorien:**
1. Prüfung der Kategorie 1
1. Prüfung der Kategorie 2

**Benötigte Produkte:**
1. Produkttest 1:
   1. Kategorien: Prüfung der Kategorie 1
   1. Preis: $ 45
1. Produkttest 2:
   1. Kategorien: Prüfung der Kategorie 2
   1. Preis: $ 56.25 

      **(Die Preise müssen den hier angegebenen entsprechen, um sicherzustellen, dass der Test ordnungsgemäß funktioniert.)**

**Warenkorb-Preisregel:**

Melden Sie sich als Administrator an und gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add new rule]**. Verwenden Sie diese Werte:

**[!UICONTROL Rule Information]:**
1. **[!UICONTROL Rule Name]**: Testen Sie kostenlosen Versand
1. **[!UICONTROL Active]**: *Ja*
1. **[!UICONTROL Websites]**: *Haupt-Website*
1. **[!UICONTROL Customer Groups]**: *NICHT ANGEMELDET, Allgemein, Großhandel, Retailer*
1. **[!UICONTROL Coupon]**: *Kein Coupon*
1. **[!UICONTROL Uses per Customer]**: *0*
1. **[!UICONTROL Priority]**: *1*

**[!UICONTROL Conditions]:**

**[!UICONTROL If ALL of these conditions are TRUE:]**


**[!UICONTROL If total amount (incl. tax) equals or greater than 100 for a subselection of items in cart matching ALL of these conditions:]**


**[!UICONTROL Category is]** *5 12 13*

Aktionen:

**[!UICONTROL Percent of product price discount]** = *10*

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei der Storefront an.
2. Hinzufügen von Produkttest 1.
3. Fügen Sie zwei Mengen des Produkttest 2 hinzu.
4. Warenkorb besuchen.
5. Wählen Sie **[!UICONTROL Check Out with Multiple Addresses]** aus.

<u>Erwartete Ergebnisse</u>:

Keine Fehler.

<u>Tatsächliche Ergebnisse</u>:

*500 Fehler*

*Nachricht: Veraltete Funktion: Die implizite Konvertierung von float 112.5 in int verliert in /app/code/Magento/SalesRule/Model/Rule/Condition/Product/Subselect.php in Zeile 214 die Genauigkeit*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
