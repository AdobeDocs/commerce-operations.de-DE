---
title: 'ACSD-44851: Kategorie mit Unterkategorien, die sich nicht öffnen oder erweitern lassen'
description: Dieser Artikel bietet eine Lösung für das Problem, dass Benutzende eine Kategorie nicht mit Unterkategorien öffnen oder erweitern können.
feature: Categories
role: Admin
exl-id: c1ad13d8-94e1-47cf-ad65-9bc5ce1c26ad
source-git-commit: a1c5898626fb8419af017a29a009a0a2c069326e
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-44851: Kategorie mit Unterkategorien, die sich nicht öffnen oder erweitern lassen

Mit dem Patch ACSD-44851 wird das Problem behoben, dass Benutzende eine Kategorie nicht mit Unterkategorien öffnen oder erweitern können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 installiert ist. Die Patch-ID ist ACSD-44851. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

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

* Adobe Commerce oder Magento Open Source On-Premise: [Quality Patches Tools > Usage](/help/tools/quality-patches-tool/usage.md) im Handbuch Quality Patches Tool.

* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im Handbuch Quality Patches Tool.
