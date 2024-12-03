---
title: 'MDVA-41046: Einfache Produkte mit benutzerdefinierten Optionen sind nicht für die Zuweisung verfügbar'
description: Der Patch MDVA-41046 behebt das Problem, dass einfache Produkte mit benutzerdefinierten Optionen nicht für die Zuweisung zu konfigurierbaren/gruppierten Produkten verfügbar sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41046. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Products
role: Developer
exl-id: 7fd7a9db-f834-4aea-a9d7-6e9535c037c8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-41046: Einfache Produkte mit benutzerdefinierten Optionen sind nicht für die Zuweisung verfügbar

Der Patch MDVA-41046 behebt das Problem, dass einfache Produkte mit benutzerdefinierten Optionen nicht für die Zuweisung zu konfigurierbaren/gruppierten Produkten verfügbar sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41046. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Einfache Produkte mit benutzerdefinierten Optionen stehen nicht zur Zuweisung zu konfigurierbaren/gruppierten Produkten zur Verfügung.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt mit anpassbaren Optionen und legen Sie einen Wert für das konfigurierbare Attribut fest.
   * Verwenden Sie *Farbe* als konfigurierbares Attribut und wählen Sie *Gelb* als Farbwert aus.
1. Speichern Sie das einfache Produkt.
1. Gehen Sie nun zur Seite Konfigurierbares Produkt erstellen .
1. Gehen Sie durch den Assistenten &quot;Konfiguration erstellen&quot;und wählen Sie *Gelb* als Attributfarbe aus.
1. Wählen Sie, ohne das konfigurierbare Produkt zu speichern, die Option &quot;Andere Produkt auswählen&quot;aus dem Dropdown-Menü &quot;Auswählen&quot;.
1. Dadurch wird ein Produktraster geöffnet, das nach dem Farbattribut Gelb gefiltert wird. Wählen Sie nun das einfache Produkt aus, das zuvor mit anpassbaren Optionen erstellt wurde.
1. Speichern Sie das konfigurierbare Produkt.

<u>Erwartete Ergebnisse</u>:

Das einfache Produkt mit benutzerdefinierten Optionen ist für die Zuweisung (im Raster sichtbar) in Schritt 6 verfügbar.

<u>Tatsächliche Ergebnisse</u>:

Der Konfigurationsabschnitt ist leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
