---
title: "MDVA-38393: Katalogregeln funktionieren für konfigurierbare Produkte nicht mehr, wenn ihr einfaches Produkt neu benannt ist."
description: Der Patch MDVA-38393 behebt das Problem, dass Katalogregeln für ein konfigurierbares Produkt nicht mehr funktionieren, wenn sein einfaches Produkt neu benannt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-38393. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-38393: Katalogregeln funktionieren für konfigurierbare Produkte nicht mehr, wenn ihr einfaches Produkt neu benannt ist

Der Patch MDVA-38393 behebt das Problem, dass Katalogregeln für ein konfigurierbares Produkt nicht mehr funktionieren, wenn sein einfaches Produkt neu benannt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-38393. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Katalogregeln funktionieren für ein konfigurierbares Produkt nicht mehr, wenn sein einfaches Produkt neu benannt wurde.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit einem zugehörigen einfachen Produkt.
1. Erstellen Sie eine Kategorie.
1. Weisen Sie der neuen Kategorie nur das konfigurierbare Produkt zu.
1. Erstellen Sie neue Katalogregeln:
   * Bedingung = Kategorie enthält \&lt;neue Kategorie-ID>
   * Aktion = 50 % Rabatt
   * Aktiv = Ja
1. Führen Sie eine Neuindizierung durch.
1. Überprüfen Sie das konfigurierbare Produkt auf der Vorderseite (der Rabatt sollte angewendet werden).
1. Überprüfen Sie die Tabelle `catalogrule_product` (für das einfache Produkt sollte ein Rabatt gewährt werden).
1. Wechseln Sie zum Administrator und ändern Sie den Namen des einfachen Produkts. Dadurch würde der Tabelle `catalogrule_product_cl` ein Datensatz hinzugefügt.
1. Führen Sie den Cron- oder den Befehl `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` aus.
1. Überprüfen Sie die Tabelle `catalogrule_product` .

<u>Erwartete Ergebnisse</u>:

Das konfigurierbare Produkt hat einen Rabatt.

<u>Tatsächliche Ergebnisse</u>:

* Die für die einfachen Produkte erstellten Discount-Datensätze fehlen in der Tabelle &quot;`catalogrule_product`&quot;.
* Das konfigurierbare Produkt am Frontend hat den vollen Originalpreis.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
