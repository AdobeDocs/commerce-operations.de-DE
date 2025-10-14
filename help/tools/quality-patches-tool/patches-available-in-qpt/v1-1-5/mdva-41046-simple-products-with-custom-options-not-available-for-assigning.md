---
title: 'MDVA-41046: Einfache Produkte mit benutzerdefinierten Optionen stehen nicht zur Zuweisung zur Verfügung'
description: Der Patch MDVA-41046 löst das Problem, dass einfache Produkte mit benutzerdefinierten Optionen nicht für die Zuweisung zu konfigurierbaren/gruppierten Produkten verfügbar sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41046. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Products
role: Developer
exl-id: 7fd7a9db-f834-4aea-a9d7-6e9535c037c8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-41046: Einfache Produkte mit benutzerdefinierten Optionen stehen nicht zur Zuweisung zur Verfügung

Der Patch MDVA-41046 löst das Problem, dass einfache Produkte mit benutzerdefinierten Optionen nicht für die Zuweisung zu konfigurierbaren/gruppierten Produkten verfügbar sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41046. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Einfache Produkte mit benutzerdefinierten Optionen sind nicht für die Zuweisung zu konfigurierbaren/gruppierten Produkten verfügbar.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt mit anpassbaren Optionen und legen Sie einen Wert für das konfigurierbare Attribut fest.
   * Verwenden Sie *Color* als konfigurierbares Attribut und wählen Sie *Yellow* als Farbwert aus.
1. Speichern Sie das einfache Produkt.
1. Navigieren Sie jetzt zur Seite Konfigurierbares Produkt erstellen .
1. Gehen Sie durch den Assistenten „Konfiguration erstellen“ und stellen Sie sicher, dass Sie *Gelb* als Attributfarbe auswählen.
1. Wählen Sie ohne Speichern des konfigurierbaren Produkts die Option „Anderes Produkt wählen“ aus dem Dropdown-Menü „Auswählen“ aus.
1. Dadurch wird ein Produktraster geöffnet, das nach dem Farbattribut Gelb gefiltert wird. Wählen Sie nun das einfache Produkt aus, das zuvor mit anpassbaren Optionen erstellt wurde.
1. Speichern Sie das konfigurierbare Produkt.

<u>Erwartete Ergebnisse</u>:

Das einfache Produkt mit benutzerdefinierten Optionen steht in Schritt 6 für die Zuweisung (im Raster sichtbar) zur Verfügung.

<u>Tatsächliche Ergebnisse</u>:

Konfigurationsabschnitt ist leer.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
