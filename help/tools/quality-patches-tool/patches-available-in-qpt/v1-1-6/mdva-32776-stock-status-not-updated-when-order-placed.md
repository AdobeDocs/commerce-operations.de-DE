---
title: 'MDVA-32776: Bestandsstatus nicht mit Auftragserteilung aktualisiert'
description: Der MDVA-32776 Patch behebt das Problem, dass der Lagerstatus nicht aktualisiert wird, wenn eine Bestellung aufgegeben, aber nicht versendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-32776. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
feature: Orders
role: Admin
exl-id: 6f872c72-c96f-4c23-b6df-44e3da3a81c2
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-32776: Bestandsstatus nicht mit Auftragserteilung aktualisiert

Der MDVA-32776 Patch behebt das Problem, dass der Lagerstatus nicht aktualisiert wird, wenn eine Bestellung aufgegeben, aber nicht versendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-32776. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Lagerstatus wird beim Aufgeben einer Bestellung, aber nicht beim Versand nicht aktualisiert.

<u>Voraussetzungen</u>:

1. Das Inventar-Modul ist installiert.
1. Nicht vorrätige Produkte anzeigen ist auf &quot;*&quot;*.

   Gehen Sie zum Festlegen **Stores** > **Konfiguration** > **Katalog** > **Inventar** > **Nicht vorrätige Produkte anzeigen** = *Ja*.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei einfache Produkte mit Menge = 11 und 22.
1. Erstellen Sie ein gruppiertes Produkt mit den einfachen Produkten, die in Schritt 1 erstellt wurden.
1. Fügen Sie gruppierte Produkte zum Warenkorb hinzu, indem Sie eine der Produktmengen auf 11 setzen und das andere einfache Produkt auslaufen lassen.
1. Schließen Sie die Kasse ab und geben Sie die Bestellung auf.

<u>Erwartete Ergebnisse</u>:

Gruppierte Produkte zeigen `out-of-stock` an, wenn zugehörige einfache Produkte nicht mehr vorrätig sind.

<u>Tatsächliche Ergebnisse</u>:

1. Das einfache Produkt mit Menge = 11 ist nicht vorrätig.
1. Das gruppierte Produkt zeigt keine *nicht vorrätig* für das Produkt mit Menge = 11 an. Wenn Sie dieses Produkt jedoch zum Warenkorb hinzufügen, erhalten Sie *Fehler „Nicht vorrätig*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
