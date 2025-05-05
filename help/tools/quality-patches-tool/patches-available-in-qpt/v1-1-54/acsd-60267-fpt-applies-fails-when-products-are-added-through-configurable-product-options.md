---
title: 'ACSD-60267: FPT wird falsch angewendet, wenn Produkte über konfigurierbare Produktoptionen hinzugefügt werden'
description: Wenden Sie den Patch ACSD-60267 an, um das Adobe Commerce-Problem zu beheben, bei dem die feste Produktsteuer (FPT) korrekt angewendet wird, wenn einfache Produkte direkt zum Warenkorb hinzugefügt werden, aber fehlschlägt, wenn dieselben Produkte über konfigurierbare Produktoptionen ausgewählt werden.
feature: Taxes
role: Admin, Developer
exl-id: 919b3b96-1995-4faf-aaf1-b5cbb20e46bf
source-git-commit: bbf7df7fdca4c11f6f268344db00e2c8643b5dce
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-60267: FPT wird falsch angewendet, wenn Produkte über konfigurierbare Produktoptionen hinzugefügt werden

Der Patch ACSD-60267 behebt das Problem, dass die feste Produktsteuer (FPT) korrekt gilt, wenn einfache Produkte direkt zum Warenkorb hinzugefügt werden, aber fehlschlägt, wenn dieselben Produkte über konfigurierbare Produktoptionen ausgewählt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) 1.1.54 installiert ist. Die Patch-ID ist ACSD-60267. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Feste Produktsteuer (FPT) funktioniert ordnungsgemäß, wenn einfache Produkte mit FPT zum Warenkorb hinzugefügt werden, aber FPT wird nicht hinzugefügt, wenn Produkte über eine konfigurierbare Produktauswahl hinzugefügt werden.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie *[!UICONTROL Enable FPT]* auf *Ja* fest, indem Sie zu *Admin* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > **[!UICONTROL Fixed Product Taxes]** navigieren.
1. Erstellen Sie ein FPT-Attribut und weisen Sie es einem *[!UICONTROL Attribute Set]* zu.
1. Öffnen Sie **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Geben Sie *[!UICONTROL Default Label]* einen Titel ein, der das Attribut identifiziert.
1. Legen Sie *[!UICONTROL Catalog Input for Store Owner]* auf *[!UICONTROL Fixed Product Tax]* fest.
1. Erstellen Sie eine neue Steuer und Zone und weisen Sie sie einer neuen *[!UICONTROL Tax Rule]* zu.
1. Erstellen Sie ein konfigurierbares Produkt mit zwei einfachen Produkten.
1. Weisen Sie nun diesen einfachen Produkten zwei verschiedene FTP-Werte zu.
1. Indizieren und überprüfen Sie die Preise in der Storefront.
1. Fügen Sie die Produkte zum Warenkorb hinzu und überprüfen Sie die Zwischensummen.

<u>Erwartete Ergebnisse</u>:

* Auf der *[!UICONTROL Catalog]* Seite werden die Preise inkl. FPT angezeigt.
* Zwischensummen im Warenkorb enthalten FTP.

<u>Tatsächliche Ergebnisse</u>:

* Auf der *[!UICONTROL Catalog]* Seite werden die Preise inklusive FTP-Wert nicht angezeigt.
* Zwischensummen und Zusammenfassung sind ungültig.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
