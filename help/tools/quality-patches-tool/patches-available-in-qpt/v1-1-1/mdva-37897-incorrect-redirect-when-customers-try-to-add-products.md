---
title: 'MDVA-37897: Falsche Umleitung beim Hinzufügen von Produkten aus „Zuletzt angezeigt“'
description: Der Patch MDVA-37897 löst das Problem der falschen Umleitung, wenn Benutzende versuchen, Produkte mit Optionen aus dem Widget „Zuletzt angezeigt“ hinzuzufügen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1 installiert ist. Die Patch-ID lautet MDVA-37897. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce Version 2.4.4 behoben wird.
feature: Products
role: Admin
exl-id: d4d1d735-38e4-455e-9045-a2443ce33851
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37897: Falsche Umleitung beim Hinzufügen von Produkten aus „Zuletzt angezeigt“

Der Patch MDVA-37897 löst das Problem der falschen Umleitung, wenn Benutzende versuchen, Produkte mit Optionen aus dem Widget „Zuletzt angezeigt“ hinzuzufügen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1 installiert ist. Die Patch-ID lautet MDVA-37897. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce Version 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf unserer Cloud-Infrastruktur 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn ein(e) Benutzende(r) versucht, ein Produkt aus dem Abschnitt Kürzlich angezeigt hinzuzufügen, für das Optionen ausgewählt werden müssen, wird der/die Benutzende zur Produktlistenseite anstelle der Produktdetailseite weitergeleitet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt mit anpassbaren Optionen (Typ: Optionsschaltfläche).
1. Konfigurieren Sie das Widget „Kürzlich angesehen“, um Produkte anzuzeigen.
1. Besuchen Sie Produkte, die anpassbare Optionen haben, sodass sie im Widget „Kürzlich angezeigt“ angezeigt werden.
1. Klicken Sie **Zum Warenkorb hinzufügen** auf eines der Produkte im Widget „Kürzlich angezeigt“.

<u>Erwartete Ergebnisse</u>:

Sie werden zur Seite mit den Produktdetails weitergeleitet, um die Optionen auszuwählen.

<u>Tatsächliche Ergebnisse</u>:

Sie werden zur Produktlistenseite weitergeleitet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce On-Premise: [Software-Update-Handbuch > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/usage) in unserer Entwicklerdokumentation.
* Adobe Commerce in unserer Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu Qualitäts-Patches für Adobe Commerce finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de).
