---
title: 'ACSD-44851: Kategorie mit Unterkategorien, die sich nicht öffnen oder erweitern lassen'
description: Dieser Artikel bietet eine Lösung für das Problem, dass Benutzende eine Kategorie nicht mit Unterkategorien öffnen oder erweitern können.
feature: Categories
role: Admin
exl-id: c1ad13d8-94e1-47cf-ad65-9bc5ce1c26ad
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-44851: Kategorie mit Unterkategorien, die sich nicht öffnen oder erweitern lassen

Mit dem Patch ACSD-44851 wird das Problem behoben, dass Benutzende eine Kategorie nicht mit Unterkategorien öffnen oder erweitern können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 installiert ist. Die Patch-ID ist ACSD-44851. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende können eine Kategorie nicht mit Unterkategorien öffnen oder erweitern.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie in Adobe Commerce Admin eine Kategoriestruktur mit zwei Stammkategorien und einigen Unterkategorien für jede dieser Kategorien.
1. Öffnen Sie die Ansicht/den Emulator für Mobilgeräte oder verkleinern Sie die Fensterbreite, bis das Layout „Mobil“ wird.
1. Öffnen Sie das Hauptmenü des Katalogs.
1. Versuchen Sie, die Stammkategorien zu erweitern.
1. Versuchen Sie, die Kategorie zu öffnen.

<u>Erwartete Ergebnisse</u>:

Die Speisekarte ist zugänglich.

<u>Tatsächliche Ergebnisse</u>:

Die zweite Ebene des Mobilmenüs wird nicht geöffnet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Quality Patches Tools > Usage](/help/tools/quality-patches-tool/usage.md) im Handbuch zum Quality Patches Tool .

* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
