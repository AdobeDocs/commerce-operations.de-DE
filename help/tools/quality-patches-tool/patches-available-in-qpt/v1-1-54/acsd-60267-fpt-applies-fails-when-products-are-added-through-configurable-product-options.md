---
title: 'ACSD-60267: FPT wird falsch angewendet, wenn Produkte über konfigurierbare Produktoptionen hinzugefügt werden'
description: Wenden Sie den Patch ACSD-60267 an, um das Adobe Commerce-Problem zu beheben, bei dem die feste Produktsteuer (FPT) richtig angewendet wird, wenn einfache Produkte direkt zum Warenkorb hinzugefügt werden, aber bei der Auswahl derselben Produkte über konfigurierbare Produktoptionen fehlschlägt.
feature: Taxes
role: Admin, Developer
source-git-commit: c18ff9dd75ec6002c6461fcd3abd98ac8b97a9f7
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-60267: FPT wird falsch angewendet, wenn Produkte über konfigurierbare Produktoptionen hinzugefügt werden

Der Patch ACSD-60267 behebt das Problem, dass die feste Produktsteuer (FPT) beim Hinzufügen einfacher Produkte direkt zum Warenkorb korrekt angewendet wird, aber bei der Auswahl derselben Produkte über konfigurierbare Produktoptionen fehlschlägt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.54 installiert ist. Die Patch-ID ist ACSD-60267. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die FPT (Fixed Product Tax) funktioniert ordnungsgemäß, wenn einfache Produkte mit FPT zum Warenkorb hinzugefügt werden. FPT wird jedoch nicht hinzugefügt, wenn Produkte über eine konfigurierbare Produktauswahl hinzugefügt werden.

<u>Zu reproduzierende Schritte</u>:

1. Setzen Sie *[!UICONTROL Enable FPT]* auf *Ja*, indem Sie zu *Admin* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > **[!UICONTROL Fixed Product Taxes]** navigieren.
1. Erstellen Sie ein FPT-Attribut und weisen Sie es einem *[!UICONTROL Attribute Set]* zu.
1. Öffnen Sie **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Geben Sie für &quot;*[!UICONTROL Default Label]*&quot;eine Beschriftung ein, die das Attribut angibt.
1. Setzen Sie *[!UICONTROL Catalog Input for Store Owner]* auf *[!UICONTROL Fixed Product Tax]*.
1. Erstellen Sie eine neue Steuer und Zone und weisen Sie sie einer neuen *[!UICONTROL Tax Rule]* zu.
1. Erstellen Sie ein konfigurierbares Produkt mit zwei einfachen Produkten.
1. Weisen Sie diesen einfachen Produkten nun zwei verschiedene FPT-Werte zu.
1. Neuindizieren und überprüfen Sie die Preise auf der Storefront.
1. Fügen Sie die Produkte zum Warenkorb hinzu und überprüfen Sie die Zwischensummen.

<u>Erwartete Ergebnisse</u>:

* Auf der Seite *[!UICONTROL Catalog]* werden die Preise inklusive FPT angezeigt.
* Die Zwischensummen im Warenkorb enthalten FPT.

<u>Tatsächliche Ergebnisse</u>:

* Auf der Seite &quot;*[!UICONTROL Catalog]*&quot; werden die Preise einschließlich des FPT-Werts nicht angezeigt.
* Zwischensummen und Zusammenfassungen sind ungültig.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.

